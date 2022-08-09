## Publish Options (Exchange Options)

#### ContentType 

Allows consumers to determine the MediaType of message body.

Therefore, we can specify that this is:
- application/json
- application/pdf

#### ContentEncoding

Tells the consumer what encoding standard message is using.

Therefore, we can specify that this is:
- gzip
- compress
- deflate

#### Timestamp

Tells when the message was published

Therefore, we can specify that this is:
- 1640030010

#### appId

Tells who published the message

Therefore, we can specify that this is:
- ShopService

#### userId

Tells who published the message

Therefore, we can specify that this is:
- Admin21

WARNING! The user id needs to be the same user id that is logged in user. Otherwise, RabbitMQ rejects the message

#### DeliveryMode

Important option. It has two possible values:
- 0 
	- it do not need to be saved on a disc before sending
- 1
	- it should be saved on a disc before it is send. Safety but more space required (and be careful of storing sensitive data)

#### Expiration

Tells RabbitMQ to discard the message if it is consumer after some period of time.

## From Fasest and Least Reliable to Slowest and Most Reliable

- No confirmations 
- Mandatory Messages 
	-only notify if the message has fail to be routed.
- Publisher Confirms 
	- forces RabbitMQ to respond with acknowledgment that it was successfully consumed 
	- downside is that RabbitMQ gives us no information about when it was received - it could be after a long time
```csharp
channel.ConfirmSelect(); //or similar option
```
- Transactions 
	- this guarantees that bunch of messages were committed to the queue or elsewhere rolled back 
	- we can start transaction, commit number of messages and then commit the translation
	- If transaction affects more than one queue then it wont be atomic, so all of messages are published or none are
	- Be careful
```csharp
channel.TxSelect();
channel.TxCommit();
channel.TxRollback();
```
- Persisted Messages

#### Publish properties:

Mandatory (give us a notification of failure)
mandatory = true







