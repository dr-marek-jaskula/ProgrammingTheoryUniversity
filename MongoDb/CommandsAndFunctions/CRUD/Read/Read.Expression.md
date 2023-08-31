## Expressions in querying data

Allows the use of aggregation expressions within the query language.

$expr -> keyword/reserved key for expressions

$expr can build query expressions that compare fields from the same document in a $match stage.

If the $match stage is part of a $lookup stage, $expr can compare fields using let variables.

he $eq, $lt, $lte, $gt, and $gte comparison operators placed in an $expr operator can use an index on the from collection referenced in a $lookup stage

### Compare to field from a single document

Documents:
```
{ "_id" : 1, "category" : "food", "budget": 400, "spent": 450 }
{ "_id" : 2, "category" : "drinks", "budget": 100, "spent": 150 }
{ "_id" : 3, "category" : "clothes", "budget": 100, "spent": 50 }
{ "_id" : 4, "category" : "misc", "budget": 500, "spent": 300 }
{ "_id" : 5, "category" : "travel", "budget": 200, "spent": 650 }
```

query
```
db.monthlyBudget.find( { $expr: { $gt: [ "$spent" , "$budget" ] } } )
```

results
```
{ "_id" : 1, "category" : "food", "budget" : 400, "spent" : 450 }
{ "_id" : 2, "category" : "drinks", "budget" : 100, "spent" : 150 }
{ "_id" : 5, "category" : "travel", "budget" : 200, "spent" : 650 }
```

Other examples (with condition)

```
db.sales.find({$expr: {$gt: [{$cond: {if: {$gte: ["$volume", 190]}, then: {$subtract: ["$volume", 10]}, else: "$volume" }}, "$target"] }})
```

