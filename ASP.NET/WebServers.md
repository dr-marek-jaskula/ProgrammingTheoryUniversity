# Web servers

Web server is a piece of a software that:
- listens on a port for request
- use transport protocol to response and send resources 

We have 65 535 ports used for a communication. If web server is configured, it listens on one or many ports.

By default: HTTP -> 80 and HTTPS -> 443

If we change the default port for HTTP or HTTPS we need to specify also a port in a url like: http://localhost:8000 (if 8000 was selected for HTTP)

One computer can have many web servers running at the same time, but they need to use different ports.

There are multiple web servers like:
- Kestrel (ASP.NET default, a part of MVC)
- IIS
- NGINX (newer, fast and slim)
- Apache (powerful, old)

IIS, NGINX, Apache are old, but tested in terms of performance and security.

## Static routing

Returning a resource from a folder is called static routing. So it is getting the resource as it is from the machine we are connecting to.
We could get a text file, image or other file that is placed on the server we are connected to.
Just like navigating to the folder on our computer and opening it.

We could do it by for example:
127:0.0.1:8000/cat.jpeg

Static routing is very fast.

## Dynamic routing

Connect to webapi and change the resource in a manner specified in a request. Therefore, we do not need to have 1000 of different
cats images but a single one and a way to differentiate it as user desires. 

The best example is to generate a response with a combination of data that user want. It is impossible to make all combination of possible data requests.

## Kestrel web server 

Kestrel web server is a free, open source, lightweight web server, shipped with ASP.NET Core.

When we create a ASP.NET Core application, Kestrel is a default web server.

Each request is served by a web server.

client -> kestrel (default) -> controller -> (logic) -> kestrel -> client

Kestrel was created by Microsoft, even when the Microsoft already had IIS (Internet Information Server).
ASP.NET Core was supposed to run cross-platform, while IIS runs only on Windows.

- Kestrel does not replace IIS. 
- Kestrel is very specific to MVC Core. 

In production we do not use only Kestrel, but a combination of a Kestrel and NGINX or Appache or IIS, done by Reverse Proxy Architecture.

## IIS server

IIS is a free, open source web server shipped with an old ASP.NET Web Form and MVC 5.
Nevertheless, IIS runs only on Windows.

## Reverse Proxy Architecture

When an end-user sends the request:
- at first the request will go to strong testes server like IIS/Apache/NGINX
- then, the request will go to kestrel
- then, the request will go to MVC
- then, the request go backwards 
- the process continues

#### Kestres is acting like a **mediator**, but also it is a part of ASP.NET Core

