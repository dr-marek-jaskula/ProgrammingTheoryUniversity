## Routing

These keys are used to smartly bind route the message
- Binding keys
- Routing keys

- Direct Exchange
	- This is similar to fanout exchange, but allows to define a *binding key*. When the message is publish with an additional *binding key* it will only be processed to they queues that are bind with exactly the same *binding key*
	- So it is fanout with additional filter it we need filtering.

1. Multiple queues can be bind to the exchange with the same **binding key**.
2. Single queue can have multiple binding.