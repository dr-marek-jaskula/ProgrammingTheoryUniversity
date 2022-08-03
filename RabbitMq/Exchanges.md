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