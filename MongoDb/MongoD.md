## Start Mongo Server

mongod is the primary daemon process for the MongoDB system

Command to start mongo server
> mongod

We can change the default port 
> mongod --port 27002

We can set log path and db path

## MongoDb as Background Service

It runs a service

Start mongoDb as a background service
> net start MonogDb

Stop
> new stop MongoDb

## MongoDb configuration file

```
storage:
  dbPath: "/your/path/to/the/db/folder"
systemLog:
  destination: file
  path: "/your/path/to/the/logs.log"
```

to use this:
mongod -f [path_to_configuration_file]