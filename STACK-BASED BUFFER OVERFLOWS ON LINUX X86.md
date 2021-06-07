---
date updated: '2021-06-07T11:49:37+02:00'

---

# STACK-BASED BUFFER OVERFLOWS ON LINUX X86

#HTB #Bufferoverflow #Linux

For code to be executed in CPU it need to first reverse a stuck or buffer in the memory.
The idea behind [[Buffer overflow]] is inserting more data input a input field then the program expected, there by overflowing the buffer that have been created and write to other registers. The goal here for a hacker is to overwrite the return address with code to execute commands as the program.

## Instruction cycle

Each [[CPU]] architecture have a different instruction cycle but can be summerized like this.

| Instruction                | Description                                                                                                                                                    |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FETCH                      | Machine instruction address is read from the Instruction address register (IAR)) It is then loaded from  [[RAM]] or cache into the instruction register (IR)   |
| DECODE                     | The instruction is decoded and start circuits to execute the instructions.                                                                                     |
| FETCH operands             | If more data have to be loaded for the command to execute it done now in the cache or ram working registers.                                                   |
| EXECUTE                    | The instruction is executed, the status register is set, which can be evaluated by subsequent instruction                                                      |
| UPDATE INSTRUCTION POINTER | if no jump instruction have was executed in the execute phase, the IAR is now increased by the length of the instruction so it point to the next machine code. |

## Memory

When a program is executed, the sections is mapped to the process, and this segments are loaded into memory as ELF file.

### Buffer

![[Pasted image 20210607114642.png]]

#### .text

Contain the assembly instruction.
Read-only to prevent processes from modifying instuction. writhing to this will result in sgement failure.

#### .data
contains variables contained by the program 

#### .bss
used by some as data segmentation, which is represented as 0-bits 

#### heap
Starts at the end of .bss and grows to higher memory addresses. 

#### stack 
Is a last-in-first-out data structure, where the return addresses, parameters and frame pointer are stored. c/c++ local varibles are stored here, code can even be copied to the stack. The stack is usually placed RAM lower area above the global and static variables. 
To get access to the stack, stack pointer is used. The allocation grows down to the lower memory address. 

## CPU 

### Data registers 

|32-bit register| 64-bit register| Description|
|---|---|---|
|EAX|RAX|Accumlator is used for input/output for airthmetic operations|
|EBX|RBX|indexing addresses|
|ECX|RCX|Counter used to rotate  instruction and counter loops|
|EDX|RDX|Data used for I/O and arithmetic operations for multiply, divide and operations involving large values|



### Pointer registers 
|32-bit |64-big | Description |
|EIP|RIP|Instruction pointer stores the offset address for the next instruction to be executed. 
|ESP|RSP|Stack pointer points to the top of the stack|
|EBP|RBP|Base pointer is also known as stack base pointer or frame pointer that points to the base of the stack|


### Stack frames
The stack starts at a higher memory and goes down as values is increased. The base pointer points to the beginning of the stack. As the stack grown it goes segmented into smaller frames, that get allocated into memory. A stack frame defines a frame of data that begins with *EBP* and end with *ESP*

```shell-session
Dump of assembler code for function bowfunc:
   0x0000054d <+0>:	    push   ebp       # <---- 1. Stores previous EBP
   0x0000054e <+1>:	    mov    ebp,esp   # <---- 2. Creates new Stack Frame
   0x00000550 <+3>:	    push   ebx
   0x00000551 <+4>:	    sub    esp,0x404 
   <...SNIP...>
   0x00000580 <+51>:	leave  
   0x00000581 <+52>:	ret    
```

To leave the stack frame, the opposite is done- 
```shell-session
(gdb) disas bowfunc 

Dump of assembler code for function bowfunc:
   0x0000054d <+0>:	    push   ebp       
   0x0000054e <+1>:	    mov    ebp,esp   
   0x00000550 <+3>:	    push   ebx
   0x00000551 <+4>:	    sub    esp,0x404 
   <...SNIP...>
   0x00000580 <+51>:	leave  # <----------------------
   0x00000581 <+52>:	ret    # <--- Leave stack frame
```

### Index registers 
|32-bit|64-bit|Description|
|---|---|---|
|ESI|RSI|Source index is used pointer from source for string operations|
|EDI|RDI|Destination is used as a pointer to a destination for string operations|


