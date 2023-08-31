# Base Commands

General commands
> help

Db commands
> db.help()

Collection commands
> db.test.help()

clear prompt:
> cls

## Databases

Switch to the database "shop" (even if it does not exists)
> use shop
 
We are switch to "shop" even if it does not exists yet. After we insert a collection it will be created automatically.

On particular database, we start commands from "db"

To delete database:
> db.dropDatabase()

To delete a collection:
> db.myCollection.drop()

Get information about database
> db.stats()

Check the datatype of something
> typeof db.numbers.findOne().a

To create a collection we use db.createCollection method. First parameter is the name of the collection and the second one is the options (validations) - see SchemaValidation