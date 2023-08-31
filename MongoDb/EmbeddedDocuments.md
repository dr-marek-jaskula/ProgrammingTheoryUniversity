## Embedded Documents

They are core features of MongoDb.

It means that documents and have inner documents. So we can nest our documents.

We can up to 100 level or nesting.

Overall document size must be at most 16mb.

We can have arrays of Embedded Documents.

This is just that, the value can be another json object
```json
{
_id: ObjectId("64ef4ce5975c782ac8de761c"),
departureAirport: 'LHR',
arrivalAirport: 'TXL',
aircraft: 'Airbus A320',
distance: 950,
intercontinental: false,
status: { description: 'one-time', lastUpdated: '1 hour ago' }
}
```