#2th Disscussion
Meeting members: Alex Nhu, Sangamesh, Dongqing, Medhabi 
## Aggregated Server for persistent data stroage or Direct pushing data to PhoneHome 
### For query support and future extension, aggregated centerized server is needed 
## Local file storage for storing collected metrics 
### Data format: json or Netfilx Altas 
#### Sangamesh is responsible for inverstigating which kind of data format for better key: value storage 
#### key: hieracial in  nodeA.components. such like QosSwitchingProfile.findAllSwitchingProfile
### Local file system 
#### suggestion: MemTable, BigQueue, LevelDB 
* MemTable 
* BigQueue 
* LevelDB
#### Commmunicaton between Centerialzed server/ PhoneHome<--- Client [Local Damon]
## Option A: DCM injected tracking componenet or Local Damon [querying from GemFire]
### Pro 
### Con: query overhead for getting count of logical entities ... ? is it very large///


