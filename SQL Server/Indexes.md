## Index types

There are two types of indexes: Clustered and Non-Clustered.

Non-Clustered indexes can also be filtered indexes or with includes.

## Indexes

They increase the performance of a SELECT statements (search queries)

They create a Balance-Tree (B-Tree) structure on our data to help us retrieve data.

The common example is the Table of Content in a book. It helps to look for data.

## Clustered Index

Only one clustered index can be present in a table.
Primary key defines the clustered index.

This is the representation of physical structure (order) of data in the table.

The leafs points to the real addresses of our data.

## Non-Clustered indexes

There can be many non-clustered indexes in one table. They use the help of clustered index to point to the data.

The leafs in balance-tree points to the clustered index nodes to located the data.

Non-clustered index are used to improve performance of a queries, mostly for a specific queries.
However, the cost is reducing the performance of INSERT, UPDATE, DELETE commands, because also the index needs to be changed.

Non-clustered index can be filtered (to not include some records) or with includes (to contain the physical data - point to it).


