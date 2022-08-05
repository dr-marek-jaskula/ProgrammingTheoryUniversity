## API

API stands for "Application Programming Interface".
It is a software that allows one piece of software to talk with another.

## Web services

Web services provide a common platform that allows multiple applications build on various programing language to gave the ability to communicate 
with each other.

Types of web services:
- SOAP
- RESTful web services

## REST

REST stand for "Representational State Transfer". 

This architectural style founded by Roy Fielding in his Ph.D. dissertation:
“Architectural Styles and the Design of Network-based Software Architectures” at UC Irvine. 
He developed it in parallel with HTTP 1.1

When the api is created using such pattern we can access images, posts, videos, text content using certain url and request verb:
- POST (update)
- GET (read)
- PUT (create)
- DELETE (delete)

We use REST primarily as a way to communicate between computer systems on the World Wide Web.

## Restful API

This is an API created using the REST architecture.
It enables web application that are build on various programming language to communicate with each other.

REST API abides by the following rules:

- Statelessness: Systems aligning with the REST paradigm are bound to become stateless. A constraint is applied by using resources instead of commands, and they are nouns of the web that describe any object, document, or thing to store/send to other resources.
- Cacheable: Cache helps servers to mitigate some constraints of statelessness. It is a critical factor that has improved the performance of modern web applications. Caching not only enhances the performance on the client-side but also scales significant results on the server-side.
- Decoupled: REST is a distributed approach, where client and server applications are decoupled from each other. Irrespective of where the requests are initiated, the only information the client application knows is the Uniform Resource Identifier (URI) of the requested resource.
- Layered: A Layered system makes a REST architecture scalable. As REST API is layered, it should be designed such that neither Client nor Server identifies its communication with end applications or an intermediary.