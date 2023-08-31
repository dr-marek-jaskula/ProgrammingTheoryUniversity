## forEach

To process each element we can use .forEach function. This will operate on the cursor.

> db.passengers.find().forEach((passengerData) => {printjson(passengerData)})