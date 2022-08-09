## Queue Options

#### auto delete

This allows us to delete a queue automatically if it is no longer needed.

A queue is only deleted when there are not consumers consuming from it.

Such queue is also called "Temporary Queue" and it is often used in applications such as chat applications or applications that use a request-reply pattern where we create queues for a time.

Auto delete is usually set with a "flag" (something like boolean value)

#### auto expire

This is similar to auto delete. The queue will be deleted but only after a certain amount of time has elapsed, where the queue is not used.

To do this we declare a queue with a "x-expires" argument, the value is a ttl (time-to-live) which tells RabbitMQ broker how long we want the queue to stay around after it is not longer being used.
The queue will then expire after certain conditions have passed, including the queue having no more consumers.

Auto expire is usually set with x-expires argument.

#### auto expire msg

This allows us to expire messages. It prevents messages from hanging around too long on a queue if they have not been consumed.

If we have Dead Letter Exchange set up and the message on the queue expires it will be send to the Dead Letter Exchange.

To do this we declare a queue with a "x-message-ttl" argument, the value is a ttl (time-to-live) for messages.

#### max length queue

This allows us to keep a limited number or messages on a queue at any one time.

So this allows us to create queues that have a known max length.

If more messages are publish to the queue than the max length enables, then we will drop messages from the front of the queue as more messages are added.

These remove messages can be dead lettered (passed to the Dead Letter Exchange)

To set this option we pass the parameter "x-max-length" 

#### exclusive 

Exclusive Queues allows only one consumer at the time to consume messages. It can only be consumed on the same connection and channel that was declared on.

It is set usually by a "flag" when creating a queue.

#### durable

durability is set by a "flag".

Durable queue will persist across server restarts.

If our broker restarts and comes back up again, the queue will still exist.

It is important option, especially in case of reliability

#### other

"x-dead-letter-exchange" to specify and configure the exchange