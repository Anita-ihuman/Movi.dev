## A Brief Understanding of HTTP

# Introduction 
If you have noticed, every website has this* “ https:”* attached to its link. I always wondered what this was all about and I bet you do too.
In this article, I will talk about the HTTP and it’s role in a webpage.
## Table of content 
- What is HTTP 
- Difference between HTTP and HTTPs
-  HTTP  request methods
- HTTP status messages
- HTTP status codes



## What is HTTP
The Hypertext Transfer Protocol (HTTP) is designed to enable communications between clients and servers. It is used by the World Wide Web to define how messages are formatted and transmitted and what actions Web servers and browsers should take in response to various commands.
HTTP works as a request-response protocol between a client and a server. Once a URL is entered into a Web browser, an HTTP command is sent to the Web server directing it to fetch and transmit the requested Web page. 

![images (1).jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1599789252871/HW98lNsX0.jpeg)
## HTTPS
HTTPS stands for HyperText Transfer Protocol Secure. Simply put, it is the secure version of HTTP. It ensures that communications between the browser and website (client and server) are encrypted by Transport Layer Security(TLS)[the successor to Secure Sockets Layer (SSL)], the standard security technology that establishes an encrypted connection between a web server and a browser. Before entering sensitive information such as credit card details or a password, check that the website is using HTTPS. If it is not, any data entered into the website will be sent in plaintext, this makes it susceptible to interception. 

![images.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1599789291763/xw9pytsyj.jpeg)
##  Difference between HTTP and HTTPs

- There is no encryption in HTTP, with HTTPS the data is encrypted before sending.


- 
HTTP sends data over port 80 while HTTPS uses port 443.

- 
HTTP is unsecured while HTTPS is secured.

- 
No SSL certificates are required for HTTP, with HTTPS it is required that you have an SSL certificate.
- 
HTTP URL in your browser's address bar is http:// and the HTTPS URL is https://.

![053018_0552_HTTPvsHTTPS1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599790244170/rqP-FOpKF.png)
## HTTP  request methods

 
1.   ** GET**:
The GET method is used to retrieve information from the given server using a given URI. Requests using GET should only retrieve data and should have no other effect on the data.

1. 
**HEAD:**
Same as GET, but transfers the status line and header section only.

1. 
**POST**:
A POST request is used to send data to the server, for example, customer information, file upload, etc. using HTML forms.

1. 
**PUT**
The PUT method is used to update the resource available on the server. Typically, it replaces whatever exists at the target URL with something else.

1. 
**DELETE**:
Removes all current representations of the target resource given by a URI.

1. 
**CONNECT**:
Establishes a tunnel to the server identified by a given URI.

1. 
**OPTIONS**:
Describes the communication options for the target resource.

1. 
**TRACE**:
Performs a message loop-back test along the path to the target resource.

## HTTP Status messages 
A typical Responses consist of the following elements:

- The *version *of the HTTP protocol they follow.
- HTTP *headers,* values that are found in a request or response.
- Optionally, a* body* containing the fetched resource.
- A* status code*, indicating if the request was successful, or not, and why.
- A *status message,* a non-authoritative short description of the status code.

![1_5QCrgA5LoA8AKR30ce6x5A.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599790002009/NZMJM1N4F.png)
## HTTP status codes
The HTTP response status codes indicate whether a particular HTTP request has been completed or not. They are grouped into five classes:

1. 
Informational responses **(100–199)**
 
1. 
Successful responses **(200–299)**
 
1. 
Redirects **(300–399)**

1. 
Client errors (**400–499)**

1. 
Server errors **(500–599)**


### Informational responses **(100–199)**:


- 
**100—Continue:** The server has received the request headers, and the client should proceed to send the request body 


- 
**101—Switching Protocols:** The requester has asked the server to switch protocols


- 
**103—Checkpoint**: Used in the resumable requests proposal to resume aborted PUT or POST requests


### Successful responses **(200–299)**:

- 
**200—Ok👍:** This response indicates the request has succeeded.


- 
**201—Created:** The requests have succeeded and a new resource has to be created as a result.


- 
**202—accepted**✅: The result has been received but has not been acted upon.

- 
**204—NO content**😢: Indicates that there is no content to send for the request but the header may be useful.


- 
**205 — Reset content🔄:** Alerts the user agent to reset the document which sent this request.

### Redirects **(300–399)**:

- 
**300 — Multiple Choices**: A link list. The user can select a link and go to that location. Maximum five addresses.  


- 
**301— Moved Permanently**⛔️:  The requested page has moved to a new URL. 


- 
**302— Found**🆕: The requested page has moved temporarily to a new URL. 

- 
**303—See Other**👁‍🗨👉🏾: The requested page can be found under a different URL.


- 
**304 —Not Modified:** Indicates the requested page has not been modified since last requested.


- 
**306 —Switch Proxy**❌: No longer used.


- 
**307 —Temporary Redirect:**	The requested page has moved temporarily to a new URL.


### Client errors (**400–499)**


- 
**400 — Bad Request **👎:
The request issued has problems (for example, might be lacking some required parameters). A good addition to a 400 response might be an error message that a developer can use to fix the request.


- 
**401 — Unauthorized** 🚫 ✖️:
Especially useful for authentication when the requested resource is not accessible to the user owning the request.


- 
**403 — Forbidden ** ⛔️:
The resource is not accessible to the client, but unlike 401, authentication will not affect the response.


- 
**404 — Not Found** 🔍  🔦:
The requested resource could not be found but may be available in the future. Subsequent requests by the client are permissible.


- 
**405 — Method Not Allowed **✖️:
The HTTP verb(e.g POST, GET, PUT etc)used on a resource is not allowed — for instance, doing a POST on a read-only resource.

- 
**409 Conflict**:
Indicates that the request could not be processed because of conflict in the current state of the resource, such as an edit conflict between multiple simultaneous updates.


### Server errors **(500–599)**

- 
**500  —Internal Server Error:**
The server has encountered a situation it doesn't know how to handle.


- 
**501  —Not Implemented:**
The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD.


- 
**502 —Bad Gateway😿:**
This error response means that the server while working as a gateway to get a response needed to handle the request, got an invalid response.


- 
**503 —Service Unavailable😑:**
The server is not ready to handle the request. Common causes are a server that is down for maintenance or that is overloaded. 


- 
**504  —Gateway Timeout⏱❗️:**
This error response is given when the server is acting as a gateway and cannot get a response in time.


- 
**505 —HTTP Version Not Supported🚫:**
The HTTP version used in the request is not supported by the server.

- 
**510 —Not Extended:**
Further extensions to the request are required for the server to fulfil it.


- 
**511 —Network Authentication Required⁉️⁉️:**
The 511 status code indicates that the client needs to authenticate to gain network access.


## Conclusion
Wow!! since you have come  this far, Congratulations 🎊🎊🎊🎊🎊 !!!!. Now you know the basics of HTTP and what it’s status codes stand for.