## Sorting results

**1** means "ascending" and **-1** means "descending**

> db.movies.find().sort({"rating.average": -1})
> db.movies.find().sort({"rating.average": 1})

Multiple sorting criteria
> db.movies.find().sort({"rating.average": 1, runtime: -1})

Mongo db automatically applies sorting before take and skip (with aggregation it is different)