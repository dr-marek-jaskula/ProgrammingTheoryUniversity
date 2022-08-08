## Request Reply Pattern

Allows to send the request into RabbitMQ, specifying the queue we would like to send to.
When the consumer consumes this message, is able to send the reply onto the other, specified queue.

Usually, the reply exchange is a default exchange, but the request one is not.

**The Reply Queue needs to be specified by a client.** 

It is specified when publishing a message onto RabbitMQ. It uses "reply_to" property to tell the server in which queue it wants a reply.

```
	  -----> exchange -----> Request Queue ----->
Client											  Server
	  <--- Reply Queue <--- Default Exchange <---
```

There reply_to=Reply Queue.

#### Main problem

If we have multiple request and replies, we must know which reply is for what request. 

To deal with this problem we add metadata in a for of **tags** to uniquely identify which reply is for what request.
Then, the server also tags its replies with the same tags. 

Basic tags:
- message_id=ABCDEF
- correlation_id=123456

Two approaches:
- Client uses "message_id" and the sever uses "correlation_id" with the same value as "message_id"
- Client and server use "message_id" with the same values.

My preference:
- Client uses "message_id" and the server uses "correlation_id" with the same value as "message_id"


