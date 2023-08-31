## Update arrays

In order to modify selected elements of the array and not to override the whole element of the array, we use:
```
db.users.updateMany({hobbies: {$elemMatch: {"title": "Sports", "frequency": {$gte: 3}}}}, {$set: {"hobbies.$.highFrequency": true}})
```

So we use the syntax of 
```
"hobbies.$.hightFrequency"
```

This **.$** means that the change will refer to the found element of the array. In this case it will add or modify .hightFrequency field.
So **$** is a special placeholder.


NOTE: the sign ```$``` refers only to the first matching element of the array.
Example for querying multiple elements but not array elements:
```
db.users.updateMany({"hobbies.frequency": {$gt: 2}}, {$set: {"hobbies.$.goodFrequency": true}})
```
There foreach matching user, only the one element of the array will be updated (added goodFrequency = true field) even if two
elements of the "hobbies" array will match.

To update all we use place holder of ```.$[]```:
> db.users.updateMany({totalAge: {$gt: 30}}, {$inc: {"hobbies.$[].frequency": -1}})

#### Update first matching element of the array: .$

#### Update all elements of the array: .$[] 

## Find and update all matching elements of the array

We add to the .%[] additional argument that can be custom named, for instance **myArrayFilter**
```
db.users.updateMany({"hobbies.frequency": {$gt: 2}}, {$set: {"hobbies.$[myArrayFilter].goodFrequency": true}}, {arrayFilters: [{"myArrayFilter.frequency": {$gt: 2}}]})
```

This filter can be different from the one to filter documents. Its just a filter for array elements of the documents.

The filter is just a variable that represent the array element

## Add elements to the array

Add element to the array id done by operator **$push**

```
db.users.updateOne({ name: "Maria" }, { $push: { hobbies: { title: "Sports", frequency: 2 } } } )
```

We can use push multiple elements using **$each** operator
We can also use $sort, to add them in concrete order. Also we can use $slice to add only a part of them
```
db.users.updateOne({ name: "Maria" }, { $push: { hobbies: { $each: [{ title: "Good Wine", frequency: 1 }, {title: "Hiking", frequency: 2}], $sort: {frequency: -1} } } })
```

## Remove elements from the array

We use **$pull** operator

```
db.users.updateOne({ name: "Maria" }, { $pull: { hobbies: { title: "Hiking" } } })
```

To remove last element of the array
```
db.users.updateOne({ name: "Chris" }, { $pop: { hobbies: 1 } })
```

To remove first element of the array
```
db.users.updateOne({ name: "Chris" }, { $pop: { hobbies: -1 } })
```

## $addToSet

This operator add only when there is no same element (add unique ones only).
```
db.users.updateOne({ name: "Maria" }, { $addToSet: { hobbies: { title: "Sports", frequency: 2 } } })
```