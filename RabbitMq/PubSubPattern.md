## PubSub Pattern

This pattern is about delivering messages to multiple consumers. 
This is almost the opposite of a Competing Consumer pattern. We send the same message to multiple consumers.

Multiple microservices may be interested in processing the same message. We do not want to process the message to every single consumer directly.

We want o decouple our producers from our consumers, so we can add a new consumers.

For that purpose we will use "fanout exchange":
- The fanout exchange just broadcasts all the messages it receives to all the queues it knows.

Now, the producer to not know what services actually consume messages - decoupling is ensured.
Therefore, producer does not declare queue. He even does not know how many queues will get his messages.

In Pub/Sub we bind the exchange to multiple queues. So only the Fanout exchange knows what queues are interested in message.

We do not need to explicit declare these queues upfront. We can use temporary queues. So when the service do not longer need messages, the queue can be destroyed.
