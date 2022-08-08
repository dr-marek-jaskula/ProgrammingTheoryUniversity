## Exchanges

They receive messages from produces and push them into queues. Exchange knows what to do with the message, for instance should it be send to single queue, to multiple queues, should it be discarded

- Default Exchange (look almost like processing the message to the queue)
- Fanout Exchange
	- The fanout exchange just broadcasts all the messages it receives to all the queues it knows.
- Direct Exchange
	- This is similar to fanout exchange, but allows to define a *binding key*. When the message is publish with an additional *binding key* it will only be processed to they queues that are bind with exactly the same *binding key*
	- So it is fanout with additional filter it we need filtering.
	- Multiple queues can be bind to the exchange with the same **binding key**.
	- Single queue can have multiple binding.
- Topic Exchange
	- messages can have an arbitrary routing key. It is a list of words delimited by dots. Usually words have some meaning connected with a system/message.
	- binding needs to have the same routing key to process the message with such routing key 
	- The real power of Topic Exchange and **routing key** is that we can use matching patterns (something like regex, see Keys)
	- Same as in a direct exchange, we can additionally use the binding keys.
- Header Exchange
	- it is similar to direct exchange. 
	- it uses a headers (parameters) to say where to route the message
	- header are key-value pairs. For instance "{'name': 'Mark'}"
	- binding parameters are used to bind the Header Exchange with a Queue. They are key-value pairs. For instance, "arguments= {'x-match': 'any', 'name': 'Mark', 'age': '47' }"
	- the binding way is defined by argument 'x-match'. If it is:
		- 'any', then if the subset or arguments matches the whole headers set, the messages is send to queue
		- 'all', then if all header key-value pairs match all arguments (excluding 'x-match' of course), then the message is send to queue. Header can have additional key-value, it will not break binding

## Exchange to exchange routing

Exchanges can not only be bound to queues, but also to other exchanges.

This gives us extra flexibility. However, it makes the system complex and simple systems are more readable and maintainable.

We can for instance:

message to:
- Direct exchange 
	- routing_key = black
		- queue1
	- routing_key = green
		- Fanout Exchange
			- queue2
			- queue3
			- queue4

## Consistent Hasing Exchange 

This is an additional exchange, that need to be installed.
Installation guide for Consistant Hashing Exchange is in 1.InstallationAndBasics

This is similar to applying the CompetingConsumerPattern (Work Queue) but it has also additional options.

We can add the routing based on some property of the message.

Binding key is a numeric value! (we are talking about binding keys between exchange and queues, not message routing keys)

The algorithm is as follows:
- Key is hashed
- based on a numeric value of binding key, the hash sets are determined. If the value is bigger, the hash set is bigger (it is value/sumOfAllValues)
	- the routing key of the message is hashed. The hash will belong to one of the sets. The probability of where it goes is determined by binding keys values

- If it is equal for all, like "routing_key=1", then the same amount of messages is passed to each queue
- If one of binding is like "routing_key=2" and other "routing_key=1", then if will receive two time more messages then other queues

