# Filters

## Operators

Range filter based on operators (keywords).

### Comparison Operators

#### Equal
> db.movies.find({name: "The Last Ship"})
> db.movies.find({name: {$eq:"The Last Ship"}})

#### NotEqual
> db.movies.find({name: {$ne:"The Last Ship"}})

#### Greater Than
> db.movies.find({runtime: {$gt:30}})

#### Greater Than or Equal
> db.movies.find({runtime: {$gte:30}})

#### Lower Than
> db.movies.find({runtime: {$lt:30}})

#### Lower Than or Equal
> db.movies.find({runtime: {$lte:30}})

#### Value in the set 
> db.movies.find({runtime: {$in: [30, 42]}})

#### Value not in the set 
> db.movies.find({runtime: {$nin: [30, 42]}})

### Filter on embedded documents 

We must use **"** when filtering on a nested property
> db.movies.find({"rating.average": {$gt: 7}})
> db.movies.find({"_links.self.href": "http://api.tvmaze.com/shows/12"})

## Logical Operators

#### Or operator
> db.movies.find({$or: [{"rating.average": {$lt: 5}}, {"rating.average": {$gt: 9.3}}]})

#### Nor operator (negate or)
> db.movies.find({$or: [{"rating.average": {$lt: 5}}, {"rating.average": {$gt: 9.3}}]})

```db.inventory.find({$nor: [{price: 1.99},{sale: true}]})```

This query will return all documents that:
- contain the price field whose value is not equal to 1.99 and contain the sale field whose value is not equal to true or
- contain the price field whose value is not equal to 1.99 but do not contain the sale field or
- do not contain the price field but contain the sale field whose value is not equal to true or
- do not contain the price field and do not contain the sale field

#### And operator
Old way
> db.movies.find({$and: [{"rating.average": {$gt: 9}}, {genres: "Drama"}]})
New way, because its by default
> db.movies.find({"rating.average": {$gt: 9}, genres: "Drama"})

New way, because its by default
> db.movies.find({"rating.average": {$gt: 9}, genres: "Drama"})

!!! Note !!!
By default if we specify the same key, one will get overrided
Therefore, the proper way is to use **$and**
> db.movies.find({$and: [{genres: "Horror"}, {genres: "Drama"}]})
This will query films that contain genre "Horror" and contain genre "Drama"

#### Not operator
> db.movies.find({runtime: {$not: {$eq: 60}}})

## Elements Operators

### Exists
Movies with runtime that exists and is greater than 30 
> db.movies.find({runtime: {$exists: true, $gt: 30}}}

Movies with runtime that not exists 
> db.movies.find({runtime: {$exists: false}}}

Movies with runtime that exists (will include null if runtime is defined)
> db.movies.find({runtime: {$exists: true}}}

Movies with runtime that exists and its not null
> db.movies.find({runtime: {$exists: true, $ne: null}}}

### Type

Let us assume that the numbers for the users can be string, int or double. Then we can filter on it.
Get users with double number
> db.users.find({number: {$type: "double"}})
Get users with int number
> db.users.find({number: {$type: "double"}})
Get users with string number
> db.users.find({number: {$type: "string"}})
Get users with string or double number
> db.users.find({number: {$type: ["string", "double"]}})
