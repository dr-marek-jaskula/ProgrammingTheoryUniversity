## Mapping/Selecting/Projecting

In MongoDb mapping at the database level is call "Projecting". 

Passengers have _id, name and age only.

Projection is the second argument of the find method
> db.passengers.find({}, {name: 1})

We would get the _id and the name only. So **1** indicates that we want to get this.

Value **0** indicates that we do not want to get this 
> db.passengers.find({}, {name: 0})

Therefore, we would get only _id and age property now.

By default _id is included. To exclude id, we must do this using 0
> db.passengers.find({}, {_id: 0, name: 1})

with embedded documents:
> db.movies.find({}, {name: 1, genres: 1, runtime: 1, "schedule.time": 1})

## On arrays

will search for movies that has both genres: "Drama" and "Horror" and return one genre last readed (so Horror)
> db.movies.find({genres: {$all: ["Drama", "Horror"] }}, {"genres.$": 1})

One condition for filtering (we filter for one having "Drama") but we return only "Horror" or nothing
> db.movies.find({genres: "Drama" }, {genres: {$elemMatch: {$eq: "Horror"}}})

result set:
```
  { _id: ObjectId("64f045bd5a846de57b90e521") },
  { _id: ObjectId("64f045bd5a846de57b90e522") },
  { _id: ObjectId("64f045bd5a846de57b90e523") },
  { _id: ObjectId("64f045bd5a846de57b90e524"), genres: [ 'Horror' ] },
  { _id: ObjectId("64f045bd5a846de57b90e526") },
  { _id: ObjectId("64f045bd5a846de57b90e527"), genres: [ 'Horror' ] },
  { _id: ObjectId("64f045bd5a846de57b90e529"), genres: [ 'Horror' ] },
  { _id: ObjectId("64f045bd5a846de57b90e52a") },
  { _id: ObjectId("64f045bd5a846de57b90e52b") },
  { _id: ObjectId("64f045bd5a846de57b90e52c"), genres: [ 'Horror' ] },
  { _id: ObjectId("64f045bd5a846de57b90e52d") },
  { _id: ObjectId("64f045bd5a846de57b90e52f"), genres: [ 'Horror' ] },
  { _id: ObjectId("64f045bd5a846de57b90e530") },
  { _id: ObjectId("64f045bd5a846de57b90e532") },
  { _id: ObjectId("64f045bd5a846de57b90e534") },
  { _id: ObjectId("64f045bd5a846de57b90e535") },
  { _id: ObjectId("64f045bd5a846de57b90e536") },
  { _id: ObjectId("64f045bd5a846de57b90e537") },
  { _id: ObjectId("64f045bd5a846de57b90e538") },
  { _id: ObjectId("64f045bd5a846de57b90e539") }
```

## Slice operator for arrays

Slice is used to get some elements of the arrays

Here we just get 2 elements of the array
> db.movies.find({"rating.average": {$gt: 9} }, {genres: {$slice: 2}, name: 1})

We can get the last two
> db.movies.find({"rating.average": {$gt: 9} }, {genres: {$slice: -2}, name: 1})

With Skip = 1 and Take = 2 
> db.movies.find({"rating.average": {$gt: 9} }, {genres: {$slice: [1, 2]}, name: 1})
