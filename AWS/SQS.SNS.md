# SQS - Simple Queue Service

1. Search for SQS and create queue

We have two types of Queues: standard and FIFO. Usually we select standard one. Standard does not ensure the first-in-first-out fashion and one processing, 
but it is super scalable, while FIFO can process only 3000 messages per second.

Tip: use Standard in 99% times and apply our own idempotency.

Properties:
a) Visibility timeout (Visibility timeout sets the length of time that a message received from a queue (by one consumer) will not be visible to the other message consumers.)
b) Message retention period (The message retention period is the amount of time that Amazon SQS retains a message that does not get deleted. )
c) Delivery delay (The delivery delay is the amount of time to delay the first delivery of each message added to the queue. )
d) Maximum message size
e) Receive message wait time (The receive message wait time is the maximum amount of time that polling will wait for messages to become available to receive.)

Button "Perge" will delete all messages from the queue.

## Dead Letter Queue

If we have the queue called "products" the dead letter queue for this queue should be names "products-dlq".

1. We should set the "Message retention period" to max (14 days).
2. We should set "Redrive allow policy" to Enabled and then set "By queue" and provide "products" queue.

Then, we go to the "products" queue and edit it, to add a dlq for it.

After that we have "Start DLQ redrive" button at the "products-dlq"

We can get there are provide max velocity (if we want to redrive gradually or use system way)

Then just use "DLQ redrive" button.

# SNS - Simple Notification Service

It is a service that provides topics, that are just same as exchanges in RabbitMq (but can distribute messages not only to queues).

SNS needs subscription to work: if you publish message to the topic, and there is no subscription, then the message is just lost.

We can have (for standard option) multiple interesting subscriptions, like SQS, HTTP, SMS, Lambda, Email and mobile application endpoints

When creating subscription we use check option "Enable raw message delivery" so we will get our messages same as we send them (no sns default wrappers)

To allow SNS to send messages to SQS we need to configure policy on the SQS level:
1. Go to SQS queue and to "Access Policy (Permissions)" tab and edit it
Add 

```
{
    "Effect": "Allow",
    "Principal": {
    "Service": "sns.amazonaws.com"
    },
    "Action": "sqs:SendMessage",
    "Resource": "arn:aws:sqs:eu-north-1:247553491424:customers",
    "Condition": {
    "ArnEquals": {
        "aws:SourceArn": "arn:aws:sns:eu-north-1:247553491424:customers"
    }
    }
}
```

To make an publisher we use NuGet Package "AWSSDK.SimpleNotificationService".

## Filtering on topics

"Subscription Policy Filter" -> "Edit".

We have two options "Subscription filter policy" and "Redrive policy (dead-letter queue)".

We can filter on message attributes or on the message body.

For instance (attributes)

```
{
  "MessageType": [ "CustomerCreated" ]
}
```

We can use also filter on body parameters of the message:
