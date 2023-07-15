## Gateway Routing pattern

Its aim is to route request to multiple services, using the single endpoint

consumer -> Gateway ->
1. -> serviceA
2. -> serviceB
3. -> serviceC

Used when we need to exposed multiple services on single endpoint. Then client will be forced to know a single endpoint.

## API Gateway pattern

Provides a single entrypoint for certain group of microservices. Similar to "Facade pattern" from object-oriented design,
but its a part of distributed system. 

consumer -> Gateway ->
1. -> serviceA
2. -> serviceB
3. -> serviceC

API Gateway sits between client application and microservices. It acts as a reverse proxy, routing request from client to services.

Can also provided features like: 
1. Authentication
2. SSL termination
3. Cache

## Backend For Fronted pattern (BFF)

Usually it not a good idea to have a single API Gateway. This pattern aims to create multiple API Gateways
based on a business boundaries of the client apps. 

client mobile app -> Gateway-Api ->
1. -> serviceA
2. -> serviceB
3. -> serviceC
1. 
client web app -> Gateway-Web ->
1. -> serviceA
2. -> serviceD
3. -> serviceC
4. -> serviceG

## Main Features of Gateways (use Ocelot)

1. Routing
2. Request and Response Aggregation
3. Load Balancing
4. Authentication
5. Authorization
6. Throttling
7. Logging and Tracing
8. Custom Middleware
