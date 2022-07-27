## Entity states

Each entity has a corresponding state, given by Entity Framework Core (ChangeTracker):

- Added
	- entity is being tracked by the context, but it does not exist in the database (yet)
- Unchanged
	- entity is being tracked by the context and it's value was not changed
- Modified
	- entity is being tracked by the context and it was changed, but changes were not applied to the database (yet)
- Deleted
	- entity is being tracked by the context and it was deleted, but the corresponding data in the database was not deleted (yet)
- Detached
	- entity is not being tracked by the context