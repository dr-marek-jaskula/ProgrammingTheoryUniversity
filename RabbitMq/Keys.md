## Keys

These keys are used to smartly bind route to the message
- Binding keys
- Routing keys

These keys are used together

## Binding key

Queues are bind to exchanges (or exchanges to other exchanges). These bindings can have binding keys. If the **routing key** of a message is same as binding key of a certain binding, then the message is processed further.

So it is like additional filtering.

1. Multiple queues can be bind to the exchange with the same **binding key**.
2. Single queue can have multiple binding.

Therefore, it is many-to-many relationship.

## Routing key

When a message is publish with an additional *routing key* it will only be processed to they queues that are bind with exactly the same *binding key*
Binding key can be a simple word but also it can be a list of words delimited by dots. Usually words have some meaning connected with a system/message.

Example of a simple world (Direct or Topic exchange): blue
Example of dot delimited key (Topic exchange): user.europe.payments

Binding needs to be the same as routing key to process the message with such routing key.
The real power of **routing key** is that we can use matching patterns (something like regex) (only for Topic exchange):

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
