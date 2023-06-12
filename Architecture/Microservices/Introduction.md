## What are Microservices

Microservices are small business services that can work together and can work independently and can be deployed
autonomously. Usually they are scoped to the single bounded context. These services communicate with each other
by talking over the network.

Advantages:
1. They can be deployed independently 
2. Opportunity to with many different technologies (technology agnostic)
3. Implementation details of each services are hidden from other services
4. Better scalability
5. Small, focused teams
6. Lower risk, because errors affect only a part of the system

So they are:
1. Small
2. Independent
3. Loosely coupled

They should have separate codebase and present their own data. 

Disadvantages:
1. For small-scale application it is extra complex
2. We need to configure each system independently
3. Required much more knowledge to build it
4. Must monitor external configurations, metrics, health-checks
5. Hard to test
6. Multiple databases, so transaction management is difficult
