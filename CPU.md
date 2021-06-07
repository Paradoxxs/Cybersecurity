# CPU 
Center processing unit 

|Instruction|Description|
|--|--|
|FETCH|Machine instruction address is read from the Instruction address register (IAR)) It is then loaded from  [[RAM]] or cache into the instruction register (IR)|
|DECODE|The instruction is decoded and start circuits to execute the instructions.|
|FETCH operands| If more data have to be loaded for the command to execute it done now in the cache or ram working registers. |
|EXECUTE|The instruction is executed, the status register is set, which can be evaluated by subsequent instruction|
|UPDATE INSTRUCTION POINTER|if no jump instruction have was executed in the execute phase, the IAR is now increased by the length of the instruction so it point to the next machine code.