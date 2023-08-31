## Create

Atomic, per document, operations are ensured. But not for bulk operations (we would need transactions for that)

To insert one document:
> insertOne(data, options)
> db.products.insertOne({ name: "A Book", price: 12.99 })

It is same as: 
> db.products.insertOne({ "name": "A Book", "price": 12.99 })

Every documents get an unique id. We do not need to use automatically generated Id. We can use our id (for instance use ULID). Generated ids use ObjectId bson type.
> db.flightData.insertOne({departureAirport: "TXL", arrivalAirport: "LHR", _id: "txl-lhr-1"})

Insert multiple data:
> insertMany(data, options)

> db.flightData.insertMany([{"departureAirport":"MUC","arrivalAirport":"SFO","aircraft":"Airbus A380","distance":12000,"intercontinental":true},{"departureAirport":"LHR","arrivalAirport":"TXL","aircraft":"Airbus A320","distance":950,"intercontinental":false}])

Note: do no use obsolete "insert" method. Use "insertOne" or "insertMany"

## insertMany default behavior

Default behavior of inserting with insertMany is to insert documents up to the error and then pass.

Example:
Let us insert
> db.hobbies.insertMany([{_id: "sports", name: "Sports"}, {_id: "cooking", name: "Cooking"}, {_id: "cars", name: "Cars"}])

Then use
> db.hobbies.insertMany([{_id: "yoga", name: "Yoga"}, {_id: "cooking", name: "Cooking"}, {_id: "hiking", name: "Hiking"}])

The result is:
```
Uncaught:
MongoBulkWriteError: E11000 duplicate key error collection: contactData.hobbies index: _id_ dup key: { _id: "cooking" }
Result: BulkWriteResult {
  insertedCount: 1,
  matchedCount: 0,
  modifiedCount: 0,
  deletedCount: 0,
  upsertedCount: 0,
  upsertedIds: {},
  insertedIds: { '0': 'yoga', '1': 'cooking', '2': 'hiking' }
}
Write Errors: [
  WriteError {
    err: {
      index: 1,
      code: 11000,
      errmsg: 'E11000 duplicate key error collection: contactData.hobbies index: _id_ dup key: { _id: "cooking" }',
      errInfo: undefined,
      op: { _id: 'cooking', name: 'Cooking' }
    }
  }
]
```

but see that:
```
[
  { _id: 'sports', name: 'Sports' },
  { _id: 'cooking', name: 'Cooking' },
  { _id: 'cars', name: 'Cars' },
  { _id: 'yoga', name: 'Yoga' }
]
```
So Yoga was added

## Override the default behavior: ordered

We cannot rollback the whole operation (for that we need transactions). 
We can make to try to insert all documents, even after the first one fails.

Add second argument: a document:
```
{ordered: false}
```

The default is ```{ordered: true}```

Then use
> db.hobbies.insertMany([{_id: "yoga", name: "Yoga"}, {_id: "cooking", name: "Cooking"}, {_id: "hiking", name: "Hiking"}], {ordered: false}})

and the hiking will be added 

## insert options: writeConcern

The whole argument:
> {writeConcern: { w: 1, j: undefined }
> {writeConcern: { w: 1, j: false }

Option **w** means "on how many instances we want this to be acknowledged". Default is 1 - "my mongoDb should accept this write".
We can make ```w: 0``` so we will have faster operation but we will not know if it succeeded or not.

Option **j** means "journal". Journal is a additional file that Storage Engine manages. It is like "ToDo file".
So it persists the operations it does not yet but want to do, like write operation. This a real file on the disc.
Hence, Storage Engine manages also in memory operations, the idea of "Journal" is that the mongoDb is aware of the 
operation it need to perform - so if for instance the server goes down, the file is still there. This is like backup.
Writing into Journal is faster then to the database (because we need to handler ordering and indexes and in the journal we 
do not need). Nevertheless, by default the Journal is not used (because it slows the operations).

To use the journal:
> { w: 1, j: true }

To use the journal with timeouts:
> { w: 1, wtimeout: 200, j: true  }
This means "how much time we give the server to return a success before we cancel the operation"


