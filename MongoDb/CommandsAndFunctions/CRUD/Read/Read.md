## Read

Read multiple documents:
> find(filter, options)

Read one data
> findOne(filter, options)

Get all products
> db.products.find()

Apply filter
> db.flightData.find({intercontinental: true})
> db.flightData.find({distance: {$gt: 10000}})

## Query 

We query data by using **find** or **findOne** methods.

## find

Function find **does not** gives us whole data.

It gives us a part of data (20 documents) and the cursor, so we can get next part of the data.
To get the next part of the data in the console, we use **it** command.

Thus, we can cursors, we can have super fast filtering and pagination.

In order to get all elements (skip cursor) we can use for instance .toArray()
> db.passengers.find().toArray()

On cursor we can use other methods

Just access a name
> db.passengers.findOne({name: "Albert Twostone"}).name

## Count results

Add at the end: .count()