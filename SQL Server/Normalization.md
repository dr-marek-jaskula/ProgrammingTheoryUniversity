## Normalization

Normalization is a database design technique to remove redundant data.

We can remove redundant data for instance by normalization the terminology:
> if we have a column with countries and we have "Poland" and "PL" we can normalize it to be "Poland" everywhere.

Usually we implement normalization by splitting table into two or more tables.

## Denormalization

Denormalization is a data design technique to improve search performance.

Here we accept that the duplicate data will occur, so we usually merge tables, because executing SELECT statements with join closes
is expensive. 

## OLTP and OLAP

OLTP stands for Online Transaction Processing  
OLAP stands for Online Analytical Processing  

When we have massive amounts of data, we do not want to have redundant data, but we also want to improve performance by design. Therefore, we crate two 
databases: OLTP database and OLAP database. 

- The OLTP is the normalized database, so we do not have redundant data, so it is normalized. On such database we perform inserts, updates and deletes. 
- The OLAP is the denormalized database, so we have duplicated data, but our queries are faster. 

Between these database we have Extraction Transformation Loading (ETL) process, which fetches the data into OLAP database.

## Types of normalization

There are three normal forms:

#### First normal form

Table is in a first normal form if a table has atomic values - it should not have reaping groups.

So we can have column "first_name" with "John" data, but not a column "name" with "John Kowalksy" or "John, Kowalsky" data.
Without first normal form we can have UPDATE, INSERT or DELETE anomalies (we would need to write complicated code).

#### Second normal form

Table is in a second normal form if a table is in the first normal form and all non-key columns should be fully dependent on the Primary Key.

There should not be a situation in which there is a composed key and a column is only related to the single primary key column.

#### Third normal form

Table is in a third normal form if it is in second normal form and there is no transient dependencies. 

It means there cannot be any not-key column that is dependent on other not-key column.

Example of no third normal form:
> In customer table we have customer and product name and product price (that is dependent on a product).

#### APT

We can remember normal forms by acronym APT:
- atomic values
- partial dependencies
- transient dependencies