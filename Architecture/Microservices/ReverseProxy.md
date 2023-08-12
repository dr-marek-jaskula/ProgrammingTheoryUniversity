## Reverse Proxy

A forward proxy, often called a proxy, proxy server, or web proxy, is a server that sits in front of a group of client machines. When those computers make requests to sites and services on the Internet, the proxy server intercepts those requests and then communicates with web servers on behalf of those clients, like a middleman.

A reverse proxy and an API gateway are similar concepts, but they serve different purposes.
An **API gateway** is a specific type of **reverse proxy** designed for managing APIs. 

The clients can only call the backend servers through the reverse proxy, which forwards the request to the appropriate server. It hides the implementation details of individual servers inside the internal network.

A reverse proxy is commonly used for:

- Load balancing
- Caching
- Security
- SSL termination

In c# we can use YARP (Yet Another Reverse Proxy) that is a Microsoft library to create a Reverse Proxy.

