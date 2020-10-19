# Read: Class 06

## http and rest

[Link to Video](https://www.youtube.com/watch?v=Q-BpqyOT3a8&ab_channel=TraversyMedia)

## http basics

[Link to Article](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)]

### HTTP: The Protocol Every Web Developer Must Know - Part 1

- HTTP stands for Hypertext Transfer Protocol. It's a stateless, application-layer protocol for communicating between distributed systems, and is the foundation of the modern web. As a web developer, we all must have a strong understanding of this protocol.
- HTTP allows for communication between a variety of hosts and clients, and supports a mixture of network configurations.
- This makes HTTP a stateless protocol. The communication usually takes place over TCP/IP, but any reliable transport can be used. The default port for TCP/IP is 80, but other ports can also be used.
- Communication between a host and a client occurs, via a request/response pair. The client initiates an HTTP request message, which is serviced through a HTTP response message in return. We will look at this fundamental message-pair in the next section.
- The Main Verbs
  1. GET: fetch an existing resource. The URL contains all the necessary information the server needs to locate and return the resource.
  1. POST: create a new resource. POST requests usually carry a payload that specifies the data for the new resource.
  1. PUT: update an existing resource. The payload may contain the updated data for the resource.
  1. DELETE: delete an existing resource.
- the Lesser Used verbs
  1. HEAD: this is similar to GET, but without the message body. It's used to retrieve the server headers for a particular resource, generally to check if the resource has changed, via timestamps.
  1. TRACE: used to retrieve the hops that a request takes to round trip from the server. Each intermediate proxy or gateway would inject its IP or DNS name into the Via header field. This can be used for diagnostic purposes.
  1. OPTIONS: used to retrieve the server capabilities. On the client-side, it can be used to modify the request based on what the server can support.
- Status Codes - With URLs and verbs, the client can initiate requests to the server. In return, the server responds with status codes and message payloads. The status code is important and tells the client how to interpret the server response. The HTTP spec defines certain number ranges for specific types of responses
  1. This class of codes was introduced in HTTP/1.1 and is purely provisional. The server can send a Expect: 100-continue message, telling the client to continue sending the remainder of the request, or ignore if it has already sent it. HTTP/1.0 clients are supposed to ignore this header.
  1. 2xx: Successful - This tells the client that the request was successfully processed. The most common code is 200 OK. For a GET request, the server sends the resource in the message body. There are other less frequently used codes:
   - 202 Accepted: the request was accepted but may not include the resource in the response. This is useful for async processing on the server side. The server may choose to send information for monitoring.
   - 204 No Content: there is no message body in the response.
   - 205 Reset Content: indicates to the client to reset its document view.
   - 206 Partial Content: indicates that the response only contains partial content. Additional headers indicate the exact range and content expiration information.
  1. 3xx: Redirection - This requires the client to take additional action. The most common use-case is to jump to a different URL in order to fetch the resource.
    - 301 Moved Permanently: the resource is now located at a new URL.
    - 303 See Other: the resource is temporarily located at a new URL. The Location response header contains the temporary URL.
    - 304 Not Modified: the server has determined that the resource has not changed and the client should use its cached copy. This relies on the fact that the client is sending ETag (Enttity Tag) information that is a hash of the content. The server compares this with its own computed ETag to check for modifications.
  1. 4xx: Client Error - These codes are used when the server thinks that the client is at fault, either by requesting an invalid resource or making a bad request. The most popular code in this class is 404 Not Found, which I think everyone will identify with. 404 indicates that the resource is invalid and does not exist on the server. The other codes in this class include:
    - 400 Bad Request: the request was malformed.
    - 401 Unauthorized: request requires authentication. The client can repeat the request with the Authorization header. If the client already included the Authorization header, then the credentials were wrong.
    - 403 Forbidden: server has denied access to the resource.
    - 405 Method Not Allowed: invalid HTTP verb used in the request line, or the server does not support that verb.
    - 409 Conflict: the server could not complete the request because the client is trying to modify a resource that is newer than the client's timestamp. Conflicts arise mostly for PUT requests during collaborative edits on a resource.
  1. 5xx: Server Error - This class of codes are used to indicate a server failure while processing the request. The most commonly used error code is 500 Internal Server Error. The others in this class are:
    - 501 Not Implemented: the server does not yet support the requested functionality.
    - 503 Service Unavailable: this could happen if an internal system on the server has failed or the server is overloaded. Typically, the server won't even respond and the request will timeout.

## what is ReST
[Link to aRticle](https://restfulapi.net/)

- REST is acronym for REpresentational State Transfer. It is architectural style for distributed hypermedia systems

### Guiding Principles of REST

1. Client–server – By separating the user interface concerns from the data storage concerns, we improve the portability of the user interface across multiple platforms and improve scalability by simplifying the server components.
1. Stateless – Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client.
1. Cacheable – Cache constraints require that the data within a response to a request be implicitly or explicitly labeled as cacheable or non-cacheable. If a response is cacheable, then a client cache is given the right to reuse that response data for later, equivalent requests.
1. Uniform interface – By applying the software engineering principle of generality to the component interface, the overall system architecture is simplified and the visibility of interactions is improved. In order to obtain a uniform interface, multiple architectural constraints are needed to guide the behavior of components. REST is defined by four interface constraints: identification of resources; manipulation of resources through 1. representations; self-descriptive messages; and, hypermedia as the engine of application state.
1. Layered system – The layered system style allows an architecture to be composed of hierarchical layers by constraining component behavior such that each component cannot “see” beyond the immediate layer with which they are interacting.
1. Code on demand (optional) – REST allows client functionality to be extended by downloading and executing code in the form of applets or scripts. This simplifies clients by reducing the number of features required to be pre-implemented.

- A REST API should be entered with no prior knowledge beyond the initial URI (bookmark) and set of standardized media types that are appropriate for the intended audience (i.e., expected to be understood by any client that might use the API). From that point on, all application state transitions must be driven by client selection of server-provided choices that are present in the received representations or implied by the user’s manipulation of those representations. The transitions may be determined (or limited by) the client’s knowledge of media types and resource communication mechanisms, both of which may be improved on-the-fly (e.g., code-on-demand).
[Failure here implies that out-of-band information is driving interaction instead of hypertext.]

#### REST and HTTP are not same

- ReST is a set of rules, HTTP is what we use to adhere to those rules

[Back to code 401 notes](../401-Javascript.md)