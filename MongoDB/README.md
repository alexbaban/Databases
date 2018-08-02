# MongoDB

MongoDB is an open source database that uses a document-oriented data model. 

Instead of storing your data in tables made out of individual rows, like a relational database does, it stores your data in collections made out of individual documents. 

In MongoDB, a document is a big JSON blob with no particular format or schema.

## Install MongoDB Community Edition on Windows
* (https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)

## Start mongod Processes

By default, MongoDB listens for connections from clients on port 27017, and stores data in the /data/db directory.

On Windows, this path is on the drive from which you start MongoDB. For example, if you do not specify a --dbpath, starting a MongoDB server on the C:\ drive stores all data files in C:\data\db

* add to the `PATH` system environment variables
  - `C:\Program Files\MongoDB\Server\4.0\bin\`
* open "Command Prompt"
  - `mongod` if `C:\data\db` exists
  - `mongod --dbpath "C:\data\db"`
  
  ## Stop mongod Processes
  
In a clean shutdown a mongod completes all pending operations, flushes all data to data files, and closes all data files. 
Other shutdowns are unclean and can compromise the validity of the data files.

* open "Command Prompt"
  - `mongo`
  - `use admin`
  - `db.shutdownServer()`
  - `quit()`
  
