## Tracking 

This is a default Entity Framework mechanism that tracks every changes made to the entities.
Tracker stores the base state of the entity and the current state of the entity. 
By this comparison Entity Framework knows if the changes were done.

Changes are implemented into the database, when the SaveChanges method is invoked.

Due to the fact that Change Tracker keeps two states, in some situations this downgrades the performance of our application.
For instance, if the data is queried for readonly purposes, there is no need for tracking. 
To obtain such behavior, we can use the *AsNoTracing* method.

We can also disable tracking mechanism on the whole db context:
> context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;