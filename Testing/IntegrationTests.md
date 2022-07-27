## Integration Tests

There are many types of integration tests. 

The most popular is **up-down** approach. It is an approach that imitates a user impact.

Integration tests give more realistic view to the behavior of our application. 

Setup and clean-up can be hard, if we do not know how to do things right.

## Scope

The scope of integration testing is:
- Call to the database
- Call to the file system
- Call to the server/api 
	- if it is not our api, we should mock it

## Steps of integration testing

- Setup
	- create a database
	- spin up a docker container
	- seed data into database
	- other configuration
- Dependency Mocking (API)
	- mock external api
- Execution 
- Assertion 
- Cleanup
	clean the database
