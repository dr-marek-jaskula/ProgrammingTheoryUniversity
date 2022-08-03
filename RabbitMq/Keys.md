## Keys

These keys are used to smartly bind route the message
- Binding keys
- Routing keys

These key can be used together

## Binding key

When a message is publish with an additional *binding key* it will only be processed to they queues that are bind with exactly the same *binding key*

So it is like additional filtering.

1. Multiple queues can be bind to the exchange with the same **binding key**.
2. Single queue can have multiple binding.

Therefore, it is many-to-many relationship.

## Routing key

It is a list of words delimited by dots. Usually words have some meaning connected with a system/message.
Example: user.europe.payments

Binding needs to have the same routing key to process the message with such routing key.
The real power of **routing key** is that we can use matching patterns (something like regex):

wildcards:
```
* - match exactly one word 
\# - match zero or more words
```

For instance:
- "user.europe.*" means any message with one word after europe.
- "*.user.purchases" means any message starting with any word and then "user.purchases"
- "*.user.*" and other
- "user.#" means any message that starts from user and then nothing or something or many words


