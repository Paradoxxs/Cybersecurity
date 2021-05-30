# Azure
#Cloud #Microsoft

Microsoft cloud solution 
Cloud computing is the process of off loading the hardware part to a 3rd party in this case Microsoft. 

## Azure monitor
Maximize the availability and performances of application and services by collecting analyzing and acting on telemetry from cloud and on-premises environments 

## Azure service

### Compute
|Service|Description|
|---|---|
  Virtual machine | Software emulation of physical computer|
| Container instances| PaaS ofering that runs container in Azure without the need for VM very similar to docker|
|Azure function|Event based code, serverless compute service|
|Kubernetes service| Manager for containerized service|
|Service fabric| system platfomr thar uns in azure or on-prem|
|Batch| Service for parallel and high-performance application|


### network

|Service|Description|
|---|---|
|Virtual network|Handling of VM network|
|Load balancer|Balance the network loads on application and service|
|Application gateway| Optimize app server while also increase security|
|VPN gateway| VPN for connecting to VM|
|DNS| [[DNS]] in cloud|
|Content deliver network|High-band content availability.| 
|DDos protection| protect against [[DDOS]]|
|Firewall| [[FIrewall]]|
|ExpressRoute|Dedicated connection|
|Traffic manager| Distrusted traffic over multiple azure regions|


### Storage

|Blob stoarge| stoarge of large objects|
|File storage| File server|
|Queue storage| message broken between application (RabbitMq)|
|Tabel storage| NOSQL|


### Databases

|Service|Description|
|---|---|
|Cosmos Database| Elastically and independently scale.|
|SQL| SQL|
|MySql|MySql|
|PostgreSQL|PostgreSQL|
|SQL VM| SQL server on VM|
|Database migration service| Migrates database to the cloud|
|Reids| service caches to reduce data usages and latency.|
|MariaDB|MariaDB|


### Web

|Service|Description|
|---|---|
|app service|Cloud web app|
|Notification hubs| send notification to any platform|
|API management| API|
|Cognitive search| managed search service|
|SignalR| Broken between frontend and backend| 


### IOT 
Internet of things 


|Service|Description|
|---|---|
|IOT central|is a fully managed global IOT SAAS solution that make it easy to connect|
|IOT edge| manage service what allow data models to be pushed onto IoT devices|


### Big data

|Service|Description|
|---|---|
|HDInsight|A fully-managed open-soruce analytics service for enterprises|
|Databricks|Apache apark based analytics service|

### AI 


|Service|Description|
|---|---|
|Machine learning| place to develop, tran and test machine learning models|
|ML studio|prebuilt ML models|


### DevOps


|Service|Description|
|---|---|
|DevTest Labs|Quickly create environments for text and demo|
|DevOps| Development pipeline tools|



### Azure 

### Azure app service
Is fully managed platform to build, deploy and scale web apps and API quickly 

work with .net, 

#### Azure SQL managed instance
Allows existing SQL server customers to lift and shift their on-prem application to the cloud with minimal application and database changes. 

fully manged and evergreen platform as a service. 
Preserves all PaaS capabilities (patching, backups) 



## Advisor
The goal is to help setup one azure enviorments to what is best practice 





## AI & MC
### Azure machine learning

### Cognitive service

### Azure bot service



## Azure marketplace
Allows customer to find, try and purchase application and services by Microsoft and Microsoft partners.

## Azure subscriptions
Azure subscriptions is the billing. 

## Azure resource manager (ARM)

### ARM template
Are JSON files that can be used to create and deploy Azure infrastructure. 
### Azure portal

### Azure powershell

### Azure CLI 

### REST clients

### Azure mobile app

### Azure cloud shell
web based cloud shell using either Bash or powershell

## Resource groups 
Is a container to manage and aggregate resources in a single unit. 
Resource can only exist in one resource group. 
can be in different regions
Resource can be moved to other resource groups. 

## Azure Resource






### Azure logic apps
Automate and orchestrate tasks business process.

### Azure container service
Are a light -weight virtuals environment that does not require operating system management and can respond to changes on demand





### Storage accounts

### Azure networking service



#### Virtual private network gateway (VPN)


### Windows Virtual Desktop
Desktop and app virtualization that runs in the cloud 
Create a full desktop virtualization. 


## Availability options
VM SLA 
99.9% SLA with premiums storage ; single VM 
99.99% Availability zones; pRotection from entire datacenter failure zone

multi-region disaster recovery
Regions pairs; regional protection 

## Regions
regions more then 64 regions in over 140 countries
Regions are made up of one or more datacenters in close proximity

### Regions pairs 
at least 300 miles of separation between region pairs
automatic replication for some service

### availability zones
Provide protection against downtime due to datacenter failure
physically seperate datacenter within the same regions 
Not all regions have the same availability. 

## Services

### IaaS
Infrastructure as a service
you config and manage the hardware for application

### PaaS 
Platform as as service
the cloud provider, e.g. of PaaSapp service and container
Prvides environment for building, testing and deploying application

### SaaS 
Software as a service
CLoud-based app over the internet : office 365

!\[\[Pasted image 20210511094655.png\]\]