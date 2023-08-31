## Aggregate

To query merged documents we use .aggregate method

In this example we aggregate book with the authors collection. Books have the authors field where _id is the reference. The result will be creators
> db.book.aggreagte([{$lookup: {from: "authors", localField: "authors", foreginField: "_id", as: "creators"}}])
We need to pass 4 parameters:
1. from -> from which collection we want related document (name of the collection)
2. localField -> where can the reference to the other collection be founded
3. foreginField -> the key of the localField 
4. as -> alias for the result

Note: the original list of keys (here authors) will be still there in the result.

### Aggregation

Shape data

1. Pipeline Stages
2. Pipeline Operators