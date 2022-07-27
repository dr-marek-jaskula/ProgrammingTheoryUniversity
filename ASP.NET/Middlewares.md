## Middlewares

Middleware is a segment of the **pipeline**, through which the incoming request is processed, before it hits the controller.
In other words: **middleware** provides the execution of a preprocessing logic. 

We can specify the segments of the pipeline just for specific requests and then it is called **filter** rather than a **middleware**.

Middleware is a class that implements the "IMiddleware" interface (it is possible to avoid this, but its a bad way of doing things).

In order to add the middleware to the project:
- At first, we register the middleware as a service using **builder.Services.AddScoped\<ErrorHandlingMiddleware\>()**
- Secondly, we configure the HTTP Request pipeline using **app.UseMiddleware\<ErrorHandlingMiddleware\>()**

The middleware configuration order is important, because it determines how the request will be processed (in which order).

The example of a useful middleware is **ErrorHandlingMiddleware**. 
Such middleware is designed to handle all exceptions and provide an elegant and clear response of standardized type ProblemDetail, which is very important for real-life api.
