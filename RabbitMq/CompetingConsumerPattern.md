## Competing Consumer Pattern

This is a common messaging pattern. It is also known as "Work Queue".
It is often used to distribute time consuming tasks among multiple workers.
This concept is important in web applications, where it is usually impossible to wait for a long task to complete during a short HTTP request window.

Another benefit of this approach is a scalability.

!**By default**, if we have multiple consumers, the tasks are distributed among them equality, despite of they processing power (analytic possibilities)
Therefore, if we have a fast consumer and a slow consumer, they will get same number of tasks, even if the slow consumer is still working on previous tasks and the fast consumer is ready for a work for a long time.

In order to overcome this problem, we use the Work Queue (Competing Consumer Pattern). 
We create a consumer pool large enough to deal with the processes and we dispatch messages to fast consumer when they are ready for a work.

It is important to set:
```csharp
channel.BasicQos(prefetchSize: 0, prefetchCount: 1, global: false);
```
It limits the number of unacknowledged messages on a channel (or connection) when consuming (aka "prefetch count"). 
prefetchCount = 1 -> This tells RabbitMQ not to give more than one message to a worker at a time. Or, in other words, don't dispatch a new message to a worker until it has processed and acknowledged the previous one. Instead, it will dispatch it to the next worker that is not still busy.
prefetchSize is the parameter to control unacknowledged messages size. A value of 0 is treated as infinite.
The server will send a message in advance if it is equal to or smaller in size than the available prefetch size (and also falls into other prefetch limits). May be set to zero, meaning "no specific limit", although other prefetch limits may still apply. The prefetch-size is ignored if the no-ack option is set. 
The server MUST ignore this setting when the client is not processing any messages - i.e. the prefetch size does not limit the transfer of single messages to a client, only the sending in advance of more messages while the client still has one or more unacknowledged messages. 

global: false -> shared across all consumers on the channel (applied separately to each new consumer on the channel)

global: true -> shared across all consumers on the connection (shared across all consumers on the channel)

Moreover, set the auto acknowledgment to false
```csharp
channel.BasicConsume(queue: "letterbox", autoAck: false, consumer: consumer);
```

autoAct = true means that every message is automatically acknowledged (as soon as we get it).
autoAct = false means we need to manually acknowledged messages
autoAct = false is better. We implement the Competing Consumer Pattern (this gives us opportunity to say the task is done)

When to use it:

1. This pattern works well if the task producer and task consumer communicate asynchronously. That is — the task producing logic doesn’t have to wait for a task to complete before continuing.
2. Tasks are independent and can run in parallel. The tasks should be discrete and self-contained. There shouldn’t be a high degree of dependence between tasks.
3. The volume of work is highly variable, requiring a scalable solution
4. The solution must provide high availability, and must be resilient if the processing for a task fails