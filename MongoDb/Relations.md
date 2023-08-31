## Relations in MongoDb

One way is to use Embedded Documents (data can be duplicated)

Other way is to use references (no data will be duplicated)

## One-To-One

For most One-To-One relationships usually use embedded documents. 

## One-To-Many

We can store ids in the array

## Many-To-Many

With mongoDb we do not need to add additional collection like in SQL.

To do this we combine the Embedded Documents approach and the reference approach:

1. Insert some products:
> db.products.insertMany([{title: "A Book1", price: 13}, {title: "Booker", price: 11}, {title: "BoomBook", price: 5}])
2. Insert customer:
> db.customers.insertOne({name: "Marek", age: 30, orders: [{productId: ObjectId("64ef6b0a975c782ac8de7643"), quantity:2}, {productId: ObjectId("64ef6b0a975c782ac8de7644"), quantity: 4}]})

Then we can insert a customer that has same order are other one (same productIds)

We can also use just Embedded Documents if I want to. But using just Embedded Documents can lead to massive data duplication.

## Tool for merging documents

Keyword: $lookup

Merge to documents in one steps instead of having two steps.

```
customers.aggregate([
{ $lookup: {
	from: "books",
	localField: "favBooks",
	foreginField: "_id",
	as: "favBookData"
	}
}])
```