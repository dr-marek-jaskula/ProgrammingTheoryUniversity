## Rename Field

To rename field we use: value of the property we change is the new property name. 
> db.users.updateMany({}, {$rename: {age: "totalAge"}})
This will not add new fields to documents that did not have that field