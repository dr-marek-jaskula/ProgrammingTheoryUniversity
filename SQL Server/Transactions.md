## Transaction

Transaction can treat multiple operations as a single operation unit.
Therefore, if at least one operation fails, then the whole operation is not performed (the rollback will be called).

We can use transaction for financial operation - if something is wrong, then the money will not be taken from the customer account.

In SQL SERVER we use 
```
BEGIN TRANSACTION [transaction_name]

//some code

COMMIT TRANSACTION [transaction_name]
```