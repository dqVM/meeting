#2th Disscussion
Meeting members: Alex Nhu, Sangamesh, Dongqing, Medhabi 
## Aggregated Server for persistent data stroage or Direct pushing data to PhoneHome 
### Different end users, Limited function for aggragation Service
### Use case of PhoneHome 
## Local file storage for storing collected metrics 

* Data format: json / Netfilx Altas 
* Sangamesh is responsible for inverstigating which kind of data format for better key: value storage 
* key: hieracial in nodeA.components.*. such like "QosSwitchingProfile.findAllSwitchingProfile"

### Local file system 
#### suggestion: MemTable, BigQueue, LevelDB 
##### functionality requirement: disk-based storage / no need for aggragation locally 
##### performance measure : write/read cost, purge 
* MemTable 
	* SQLMemTable is a simple and fast in-memory database for Delphi and C++ Builder.
	* SQLMemTable Free is free for personal use. Any company must order SQLMemTable Com, Pro, Team4, Team8 or Enterprise to use it in its projects

* BigQueue 
	* Big queue is extremely fast, only limited by network and disk IO bandwidth, while at the same time it’s persistent and reliable, this makes big queue a nature fit for log data collecting and analysis.
	* Performance: 
		In concurrent producing and consuming case, the average throughput is around 166M bytes per second.
		In sequential producing then consuming case, the average throughput is around 333M bytes per second

* LevelDB

	LevelDB is a fast key-value storage library written at Google 
	that provides an ordered mapping from string keys to string values.
	
#### Commmunicaton between Centerialzed server/ PhoneHome<--- Client [Local Damon]
## Option A: DCM injected tracking componenet vs  Local Damon [simply querying from GemFire]
### Pro 
### Con: query overhead for getting count of logical entities 


