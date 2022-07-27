## HTTP

HTTP is a protocol that defines rules for communication in the Internet.

HTTP is by default at port 80 and it's encrypted version is at the port 443.

HTTP protocol defines:
- how the request should be send
- what is required in the request
- on which port should the request be sent
- the form of response

Web browsers and API's should follow the HTTP rules.

#### Request

HTTP works in the following manner:  
https://youtube.com/results?search_query=webapi  
where:
- https	
	- is a protocole
- youtube.com
	- is a domain
- results	
	- is a path
- search_query
	- is a parameter name
- webapi
	- is a parameter value

Plus HTTP verb like "GET"
Plus Headers like "Accept-language: pl-PL"
Plus Request bod like "{"sortBy": "date"}"


##### HTTP request blueprint:
```
Request_verb path HTTP/version
Host: address_of_source:port
Header_in_form_of_key_value_pairs

body_of_a_request.
```

##### HTTP request example:
```
GET /orders/123 HTTP/1.1
Host: 127.0.0.1:8000
User-Agent: Manual-Http-Request
Content-Length: 12
Content-Type: application/x-www...

order_id=123
```

#### Respone

Response from the server will have:
- status code	
- headers
- response body (for instance HTML or JSON)

##### HTTP response blueprint:

```
HTTP/version status_code status_response
Header_in_form_of_key_value_pairs

body_of_a_response.
```

##### HTTP response example:

```
HTTP/1.1 200 OK
Content-Length: 88
Content-Type: text/html
Connection: Closed

<!doctype html>
<html lang-"en">
	<head>
		<meta charset="utf-8">
		<title>Title</title>
	</head>
	<body>
		<h1>Hello, World!</h1>
	</body>
</html>
```

##### HTTP response example 2:

```
HTTP/1.1 200 OK
Content-Length: 30
Content-Type: application/json
Connection: Closed

{
	"message": "Hello World"
}
```

#### Communication

This type of communication is stateless, so each request is independent form the other one. In order to simulate the state, the browser needs to send proper headers about the logged user, for example by bearer tokens.

#### Verbs

- GET - Downloading resources from the server
- POST - Creating new resources
- PUT - Updating resources (all properties)
- PATCH	- Updating resources (partially, so can update only selected properties)
- DELETE - Deleting resources

There are other verbs also, but mostly our API (REST one) will need to apply only these verbs.

#### Status codes

- Information codes 1xx:
	- 100 (Continue) - Response for further requests
	- 101 (Switching Protocols)	- Change in the protocol
	- 110 (Connection Time Out)	- Connection time was exceeded. Server not responding
	- 111 (Connection refused) - Server refused to response
- Successful codes 2xx:
	- 200 (OK) - Retuning requested resources (most common)
	- 201 (Created)	- Uploaded document was saved on the server
	- 202 (Accepted) - Request was accepted to be served, but it will take some time
	- 203 (Non-Authoritative Information) - Response is not precisely what was asked for but was created from the local or external copies
	- 204 (No content) - Server served the request and does not need any additional data
	- 205 (Rest Content) - Client should restore base document 
	- 206 (Partial Content) - Only a partial data is send. Specify "Content-Range" Header about byte range to return
- Redirection codes 3xx:
	- 300 (Multiple Choices) - There is more then one way to served the request. Server can give the way to specify the intentions
	- 301 (Moved Permanently) - The requested resource changed the URL and should be search there
	- 302 (Found) - The resource is temporarily under other URL but in future is should be found here
	- 303 (See Other) - The resource is under other URL and client should go there. This is a proper way for POST request
	- 304 (Not Modified) - The resource can not be modified as the client intended to
	- 305 (Use Proxy) - Use proxy server, that was specified in a Location response Header 
	- 306 (Switch Proxy) - Old code, for obsolete protocols
- Client Error codes 4xx:
	- 400 (Bad Request) - The request syntax is wrong
	- 401 (Unauthorized) - The resources require authorization
	- 402 (Payment Required) - Google Developer API use this code if the programmer has exceeded the request daily limit
	- 403 (Forbidden) - The resource is forbidden to be retrieved
	- 404 (Not Found) - There is no requested resource under this URL
	- 405 (Method Not Allowed) - The method in the request in not supported. In the response there are supported methods
- Server Error codes 5xx:
	- 500 (Internal Server Error) - Server encounter the unexpected error 
	- 501 (Not Implemented) - Server has not the requested function
	- 502 (Bad Gateway) - Intermediate Server get incorrect response from the main server
	- 503 (Service Unavailable) - Server can not do the work at this time, due to the server overload
	- 504 (Gateway Timeout) - Intermediate Server does not obtained the response from the main server in a requested time period