## Identity column

Identity column is the column with an IDENTITY attribute. 

If a record is added, then it is automatically incremented by the value we specified, starting from the set initial value:
> IDENTITY(InitialValue, IncrementValue).

 The SQL Server documentation clearly states that uniqueness must be enforced by using a primary key, unique constraint 
 or unique index. Therefore, to guarantee that an identity column only contains unique values, 
 one of the mentioned objects must force uniqueness for each value in an identity column.

In order to insert a record with a custom identifier we first need to:
> SET IDENTITY_INSERT [ database. [ owner. ] ] { table } { ON | OFF }

In order to check the level of identity in SQL SERVER we can:
> SELECT IDENT_CURRENT(table_name)

We can also use:
> SELECT @@IDENTITY 
This returns the last auto-incremented value in the whole database