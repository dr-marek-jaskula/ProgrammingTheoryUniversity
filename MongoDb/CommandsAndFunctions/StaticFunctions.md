## Static functions

We can use printjson static function to print document in json 
> db.passengers.find().forEach((passengerData) => {printjson(passengerData)})