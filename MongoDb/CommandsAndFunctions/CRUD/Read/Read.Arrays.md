## Arrays

> db.passengers.updateOne({name: "Albert Twostone"}, {$set: {hobbies: ["sports", "cooking"]}})

access
> db.passengers.findOne({name: "Albert Twostone"}).hobbies

to query by array (if the array contains "sports")
> db.passengers.findOne({hobbies: "sports"})

equality on arrays means "Contains"
> db.movies.find({genres: "Drama"})

for exact equality we make equality to the array
> db.movies.find({genres: ["Drama"]})

### Array of complex objects

array: "hobbies" of structure { "title": string, "frequency": number }

We want to query ones with hobby titles equal to "Sports"

Syntax (very useful mongoDb approach):
> db.users.find({"hobbies.title": "Sports"})

## On array size

> db.users.find({hobbies: {$size: 3}})

$size does not accept ranges of values. To select documents based on fields with different numbers of elements, create a counter field that you increment when you add elements to a field.

## $all

When order does not matter, but all needs to be in the array.
> db.movies.find({genres: {$all: ["Drama", "Fantasy"]}})

## $elemMatch

In order to apply condition to a document in the array we should use $elemtMatch
> db.users.find({hobbies: {$elemMatch: {title: "Sports", frequency: {$gte: 3}}}})

So now, we have that object from hobbies must have title "Sports" and the frequency greater than or equal 3.

If we would not use $elemMatch, then we could have user that has a one hobby "Sports" with frequency 2 and "Cooking" with frequency 5