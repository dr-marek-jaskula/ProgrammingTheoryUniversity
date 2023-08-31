## Upsert

To upsert we can using third argument
> db.users.updateOne({name: "Maria"}, {$set: {age: 29, hobbies: [{title: "Good food", frequency: 3}], isSporty: true}}, {upsert: true})

This will add also values on which we filter on and can be set (like equality).