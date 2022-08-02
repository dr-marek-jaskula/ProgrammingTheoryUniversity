## Installation guide for RabbitMq

1. RabbitMq is made using Erlang language. Therefore, we need to install erlang at first:
[Goto] (https://erlang.org/download/otp_versions_tree.html)

2. Set the environment variable ERLANG_HOME point to folder in which we installed erlang
	- System and Security -> System -> Advance system settings -> Environment variables
	- Create a new environment variable called "ERLANG_HOME" with value like "C:\Program Files\Erlang OTP"
	- Verify the environment variable by "echo %ERLANG_HOME%"

3. Install RabbitMq

4. Use rabbitmq-command-prompt

5. Type
> rabbitmq-plugins enable rabbitmq_management

6. Go to: localhost:15672

7. The default rabbitmq password and login is "guest"/"guest"

> We can use Chocolatey or docker image to install it

## RabbitMQ

RabbitMQ is a most popular, open-source message broker. It is a tool to govern the data flow between microservices. 

RabbitMQ communication is synchronous: we do not need to wait for the reply.

Terminology:
1. Producer - message sender
2. Consumer - message receiver 
3. Exchange - this is a system that deals with the decision about the message delivery. There can be many exchanges for many scenarios.
4. Queue - this is a system of storing the messages in a way that allows the consumer to consume it when it is possible from the consumer perspective.
5. Connection - any consumer or producer should open a single TCP connection to the RabbitMQ, but a connection can have multiple channels
6. Channel - different channels allows for instance to use different threads to push messages. Different channels results in isolating the messages from different threads.

- Producer always sends the message to the exchange.
- Exchanges push massages into one or more queues. 
- Queues are bind to the exchange. Exchange can be bind to many queues, but queue can be bind to many exchanges (many-to-many relationship). There can be a queue that is not binded to any exchange
- Messages are in a queues until they are used or consumed.
- Consumer may listen to many queues, to single queue or not listen to any queue.
 
We can have multiple producers and consumers for one message broker.

## Advance Message Queuing Protocol (AMQP)

It is an open standard for passing business messages between application or organization.  
Many message brokers use AMQP.

Exchange is like a class with methods (commands). 
When the command is send all the data that is required to execute the command is stored in so called **frame**. 
Frames have standardized structure, but there are some types of frames.

There are 4 types of frames:
- Method Frame
- Content Header Frame
- Body Frame
- Heartbeat Frame

Frame common structure:
- 1 byte: each frame starts with a byte that determines the frame type. For instance 1 is for method frame
- 2 bytes: are used to determine the channel that the frame is being sent on
- 4 bytes: represent the size of the message
- Frame Specific Content
- 1 last byte: frame end byte is used to verify that the data is not corrupted (data was of give size)

Frame Specific Content:
- number of bytes that represent the class and question (for instance 40 for exchange)
- number of bytes that represent the method (for instance 10 for declare for exchange class)
- number of bytes that represent arguments for a specific class.method we have selected
	- each argument has a certain name and a value. 
	- It needs to be passed in a specific order

Class and method id's can be found in "https://www.rabbitmq.com/resources/specs/amqp-xml-doc0-9-1.pdf"
For instance class 40 is "exchange" and method in that class with id "10" is "declare" so it "verify exchange exists, create if needed"

Then, we send to RabbitMQ is always the Method Frame. 

## Negotiations

First that happens in any connection:
- Sent Content Header Frame (it has a massage properties: how big the message is and how many body frames will be send). This is also known as Protocol Header.
- This is the only data the client sends that is not formatted as a method.
- It consist "AMQP" followed by a constant. Then, the protocol major version, protocol minor version, protocol revision
	- For instance "AMQP0091"
	- Then, server accepts or rejects the protocol header. 
	- If it reject the protocol header, it write a valid protocol header to the TCP socket and then closes the socket. 
	- If it accepts the protocol header, it implements the protocol accordingly. In this case, by responding with "Connection.Start" method frame. This method starts the connection negotiation process by telling the client the protocol version that the server proposes and list of security mechanism with a client can use for authentication. It also contains a list of server properties.
- When the client receives this he reposes with Connection.Start-OK that contains a security mechanism.
- The server sends the client a connection secure method. (To have the way to provide authentication)
- Client sends the connection secure ok method with some data to further being authenticate.
- Then server sends the "Connection.Tune" method frame. It contain various details about server connection, like maximum frame size supported, heartbeat delay
- Client responses with "Connection.Tune-Ok"  
- Then client send another message "Connection.Open" to open the connection itself. 
- The server responses with "Connection.Open-Ok" frame and the connection is ready for use

```
Client                   Broker (server)
		Protocol Header
-----------------------------> 
		Connection.Start
<-----------------------------
		Connection.Start-Ok
----------------------------->
		Connection.Secure
<-----------------------------
		Connection.Secure-Ok
----------------------------->
		Conection.Tune
<-----------------------------
		Connection.Tune-Ok
----------------------------->
		Connection.Open
----------------------------->
		Connection.Open-Ok
<----------------------------
```

## Working Connection

Simple example:
For instance we sent the Queue.Declare frame
Server will response with Quenue.Delcare-Ok or with en error and closing the channel

More complicated example:

Client					Server
		Basic.Public
----------------------------->
	Content Header Frame
----------------------------->
			Body
----------------------------->
			...
----------------------------->
			Body
----------------------------->

The reviving or consigning the messages.
There are two main approaches in RabbitMQ:
1. Use the Basic.Get method
	- This method provides the direct access to the messages in a queue by using a synchronous dialog that is design for a specific types of applications, where synchronous functionality is more important then performance.
The server will response with Basic.Get-Ok or Basic.Get-Empty, depending on it if there was a message in a queue  

Client					Server
		Basic.Get
------------------------------>
Basic.Get-Ok or Basic.Get-Empty
<------------------------------
	Content Header Frame
<-----------------------------
			Body
<-----------------------------
			...
<-----------------------------
			Body
<-----------------------------

OPTIONALLY at the end (Basic.Ack to acknowledged the received of the message unless the no-acknowledge option was set in a get method):
			Basic.Ack
----------------------------->

2. Use the Basic.Get method is not a ideal way to obtain a message from RabbitMQ. We should consume messages and not get them.
To do this the client can use the Basic.Consume method frame to the server (transient request for a messages from a specific queue)
Consumer lasts as long as the channel that was declared or until client cancels them.

Client					Server
		Basic.Consume
------------------------------>
		Basic.Consume-Ok
<-----------------------------
		Basic.Deliver
<-----------------------------
	Content Header Frame
<-----------------------------
			Body
<-----------------------------
			...
<-----------------------------
			Body
<-----------------------------

OPTIONALLY at the end (Basic.Ack to acknowledged the received of the message unless the no-acknowledge option was set in a get method):
			Basic.Ack
----------------------------->

Then, when to the queue the next message is send, then automatically the next Deliver is done:
		Basic.Deliver
<-----------------------------
	Content Header Frame
<-----------------------------
			Body
<-----------------------------
			...
<-----------------------------
			Body
<-----------------------------

It continues until channel exists or client use cancel option