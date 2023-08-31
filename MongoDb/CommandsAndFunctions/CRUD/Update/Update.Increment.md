## Increment

Increment age by 2
> db.users.updateOne({name: "Manuel"}, {$inc: {age: 2}})

Decrement age by 2
> db.users.updateOne({name: "Manuel"}, {$inc: {age: -2}})

Increment and set in one go:
> db.users.updateOne({name: "Manuel"}, {$inc: {age: 1}, $set: {isSporty: false}})

## Min, Max, Mul

Min changes the value only when the new value is lower than current value:
> db.users.updateOne({name: "Chris"}, {$min: {age: 35}})

Mul changes the value by multiplying by given value (for instance by 1.1)
> db.users.updateOne({name: "Chris"}, {$mul: {age: 1.1}})
