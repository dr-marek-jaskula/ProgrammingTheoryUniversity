## Aggregation Pattern

This pattern is useful when a client must make multiple calls to different backed systems to perform an operation. 

An application that relies on many services to perform a task must expend resources on each request. When any new feature or service is added to application,
additional request are needed.

This can impact the performance and scale of the application. 

As a solution of that, use a gateway, that will call all required services, get all responses, aggregate them and then send the response to the user.

application -> Gateway 

1. -> Service1 -> Gateway
2. -> Service2 -> Gateway
3. -> Service3 -> Gateway

Gateway -> Application

