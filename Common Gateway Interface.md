---
date: 2025-09-30
tags:
  - distrubutedsystems
---
Standardised interface between web server (HTTP-Daemon or Web­Listener) and a server-side backend program. 
Basically, a web user submits for example a web form. The data from the form is sent to the web server within HTTP request with a URL
denoting a CGI script. The CGI script then launches a new computer process, passing the form data to it as arguments and relays back the output as the 
response to the browser. 

Because CGI scripts always need to run in separate processes every time, various alternatives were developed. 

### Purpose
Traditionally, a web server has a directory which is designed as a document collection that are sent to the client. 
For pages created on the fly, the server software may defer requests to separate programs and relay the results back to the client. 
Such programs require some additional information to be specified with the request, such as query strings or cookies. 
Initially, there were no such standard ways of data exchange between a browser, HTTP server and server-side code.
As a result, mutual incompatibilities existed between different HTTP server variants. This led to the development of CGI. 
Web page-generating programs invoked by server that adheres to the CGI specification are known as CGI scripts, even if they are written
with a non-script language such as C. 
NodeJs based server support CGI scripts with an extension. 

### Example
A web server that supports CGI can be configured to interpret a URL with CGI script reference in it. 
```http://example.com/cgi-bin/printenv.pl/with/additional/path?and=a&query=string```
The output of the script is simply send to standard output and the HTTP server picks this. 
Data to the script is passed by CGI specifying a way of setting environment variables that are then picked up by the CGI script.

### Alternatives
- Web Server Gateway Interface (WSGI) is a modern approach using the python programming language.
- Jakarta EE runs Jakarta Servlet applications in a web container to server dynamic content and optionally set static content which replaces the overhead of creating and destroying processes with 
a much lower overhead of creating and destroying threads. 
