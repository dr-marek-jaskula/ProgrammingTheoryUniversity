## Indexes

Without the indexes mongoDb will performance **collectionScan** - go for entire collection and see for the 
queried document.

This is the default approach.

We can create an index which is an ordered list of all the values that are placed in the given key (field) for all documents.
Every index has also a pointer to the whole document it belongs to.

Example:
```
db.products.find({seller: "Max"})

Products seller index:
1. Anna
2. Chris
3. Manu
4. Manu
5. Max
6. Max
```

Then mongoDb will perform **index scan**. This will be very fast because, for instance if we 
look for seller "Max" it just need to check first letter and compare it with first letter of the 
item on the list, to go further if it does not match. Because of the order, after if find 
for instance 3 items, it does not move further because it know there further there are no
matching elements.

This speed queries.

## Index cost

Performance cost of the index id on the insert and update level. 