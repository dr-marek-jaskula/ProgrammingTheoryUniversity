## Update

> updateOne(filter, data, options)
> updateMany(filter, data, options)
> replaceOne(filter, data, options)

The important reserved word to set or override the value (update) is **$set**.
By this we say, that if there is no such key-value pair, we will add this. It if exists we will override this
>  db.flightData.updateOne({distance: 12000}, {$set: {marker: "delete"}}}

To update all:
> db.flightData.updateMany({}, {$set: {marker: "toDelete"}})

DO NOT USE "update" instead of updateOne or updateMany
> db.flightData.update({_id: ObjectId("64ef4ce5975c782ac8de761b")}, {$set: {delayed: true}})

The difference with update and update many is that if {$set} is not specified, the document will be replaced instead of updated. So for instance just the _id will remain.
If we want to replace something, just use replaceOne

When we use 
> db.users.updateOne({_id: ObjectId("64f0813df89c50ad00e08261")}, {$set: {hobbies: [{title: "Sports", frequency: 5}, {title: "Cooking", frequency: 3}, {title: "Hiking", frequency: 1}]}})

We would override hobbies. Other fields are not affected.
 
Update multiple fields with **$set**
> db.users.updateOne({_id: ObjectId("64f0813df89c50ad00e08261")}, {$set: {age: 40, phone: 42342342}})
