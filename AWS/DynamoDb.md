## DynamoDb

NuGet: "AWSSDK.DynamoDBv2"

1. This is document based database. 
2. It is fully managed
3. It is fast, predicable performance
4. Stores encrypted data
5. Support on demand backups
6. Key-Value based

The top level datastore is **table**, inside we have many **nodes** that are designed to scale as database get bigger.

We can configure on the table level the amount or read and writes per second. WE can also configure this to adapt to changing traffic.

It can duplicate database to get certain client the best latency.

Table is similar to SQL Database, so we can have multiple data structures there.

## Put

Put in DynamoDb is an Upsert.

## Attributes

We can think of them as a json objects (DynamoDb has its own json format. For instance "S" means string)

In DynamoDb there are only one type of keys with two forms. There is only Primary Key and it can be 
1. Partition Key
2. Partition Key + Sort Key

### The partition key

If the Primary Key of a Table is only a Partition Key, then it is Unique in the whole table.

Note: **For Partition Key we can use string, number or binary types, but it is preferred to use string**

This is the most important choice to make when designing the database:
From outer perspective we see only a Table, but inside there are multiple nodes (servers). So it is effectively a cluster.

In order to make the database scalable and be able to grow fast the Partition Key is hashed and based on a system, each nodes has the hashed range that it stores.

Therefore, SDK will know by default in each server (node) the data is stored.

Values with the same partition key can have a maximum size of 10 GB, we never query for more than 10 GB.

> On every operation that we are doing we provide the partition key with that operation.

Therefore, we never do **scanning** or cross partition querying.

**The partition key can not change**. It is immutable.

### The sort key

If the Primary Key of a Table is Primary Key + Sort Key, then the combination of two values is Unique.

Sort Key is a Key that goes with the document both with Partition Key.

Many items can have same partition key but different sort key.

Values that have the same **partition key** will be sorted using the **sort key**.

Users tend to use dates for the sort key.

## Capacity

We pay for GB of database and also for:
1. Total read capacity units 
2. Total write capacity units

We have three types of reads:
1. Strongly consistent reads
2. Eventually consistent reads
3. Transactional reads

For items up to 4 KB one read capacity unit, can perform one strongly consistent read per second. 
This value is halved if we used eventually consistent reads (0.5).
Transaction read are double (we pay 2 instead of traditional one)

The bigger the items is (over 4KB) more capacity units will be used.

We have two types of writes:
1. Normal writes
2. Transactions

One capacity unit for writes 1 KB per second. 
Transactions writes are doubled.

We can use "Auto Scaling" so to change capacity based on a traffic. 

## DynamoDb Streams

Export and streams -> DynamoDb stream details

It allows to consume database changes as the are happening:
so they are just triggers, for example when record is inserted, then send an email.
So we can notify some service. We can select:

1. Only PK and SK are in the notification
2. New image (entire item)
3. Old image (item before the change)
4. New and old images

## Auto scaling 

Define an lower and upper limits.
It collection metrics every 2minutes and scale on this.
This will also give a reserved pack of capacity to react on changes.
Downscaling algorithm is based on 15min metrics.

Target utilization is responsible for a reserved pack.

## Transactions

We can get transaction the are also cross table

## Global secondary Index (GSI)

It duplicate data for every index (so pay for more data also). [it is a table synchronized with other table]

Go to DynamoDb table and then to "indexes".

When we create index we create an "global secondary index".

Then we can set PK and SK like
"Email" and "Id"
index name = "email-id-index

## Local secondary Index (LSI)

Focus on single partition key but on multiple sort keys. It is like a secondary sort key

## Pricing Tips

1. Smaller attribute names 
2. Never try to store a file in DynamoDb (use S3 for this)
3. Always prefer Queries over Scans and point reads over both of them
4. Try to avoid strongly consistent reads and transaction as much as possible
5. Try to avoid GSI and LSI
6. On Demand Capacity only on unpredictable situation (prefer auto scaling)