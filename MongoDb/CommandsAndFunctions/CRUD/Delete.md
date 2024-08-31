## Delete

> deleteOne(filter, options)
> deleteMany(filter, options) 

to delete all
> deleteMany({})

delegate all documents in the collections
> db.users.deleteMany({})

delegate collection
> db.users.drop()
