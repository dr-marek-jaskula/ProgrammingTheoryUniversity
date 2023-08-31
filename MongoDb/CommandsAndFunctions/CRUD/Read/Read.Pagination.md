## Skip

Skip 100 documents
> db.movies.find().sort({"rating.average": 1, runtime: -1}).skip(100)

## Limit

Limit 10 documents
> db.movies.find().sort({"rating.average": 1, runtime: -1}).skip(100).limit(10)