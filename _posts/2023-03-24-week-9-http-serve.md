---
layout: post
title: Week 9 - Web Servers
date: 2023-03-25 23:59 +1100
categories: 23T1
expires: 2023-09-09 23:59:59 +1100
---

- TOC
{:toc}

## Networks

A group of computers connected together so they can communicate.

### Internet

The internet is built on global infrastructure that connects smaller networks together.

### World Wide Web

A subset or section of the internet that is made up of a system of documents and other resources, accessible by Uniform Resource Locators (URLs).

## Protocols

As there are many computers connected to the internet, they all need to agree on a method of communicating to each other.

We call these methods protocols, and every computer is must use the IP suite (Internet Protocol).

We divide the IP suite into multiple layers to represent each step in sending data over the internet. Each layer will then have multiple different protocols which can all be used.

### Application Layer

The application layer is responsible for how software can communicate over the Internet. Protocols such as HTTP, HTTPS, FTP, DNS, IMAP, POP, SMTP, SSH and TLS/SSL all are a part of this layer.

HTTP and HTTPS: HyperText Transfer Protocol (Secure) are responsible for sending text (v1) and later other files for websites/webpages.

FTP and SFTP: (Secure) File Transfer Protocol is used to send files of any kind over the internet, like using Google Drive to back up files, but directly from one computer to another.

DNS: Domain Name System translates website links into IP addresses.

IMAP: Internet Message Access Protocol, POP: Post Office Protocol and SMTP: Simple Mail Transfer Protocol are all used for email.

SSH: Secure SHell is used for making an encrypted connection to another computer, along with TLS/SSL: Transport Layer Security/Secure Sockets Layer.

### Transport Layer

This layer of protocols represents how data from the Application layers transmitted though the "fabric" of the internet without losing andy data. Protocols such as TCP and UDP make up this layer.

TCP: Transmission Control Protocol allows the source and destination computers to know if a transmission has been successfully sent and received. TCP is used in almost every case, as such, the IP system is often called TCP/IP. TCP relies on a system of handshakes/question and response messages to ensure that every packet of data is received.

UDP: User Datagram Protocol instead of using handshakes sends all of the data in one go, like a hose. This is faster than TCP, but any lost packets are not resent.

![TCP vs UDP]({{site.baseurl}}/assets/img/TCPUDP.jpg)

### Internet Layer

This layer is responsible for making sure that computers are able to find each other on the internet. The IP: Internet Protocol is part of this layer, and is designed to assign a "unique" address to each device that is connected to the internet. When we want to connect to that device, we can use the IP address.

### Link Layer

The link layer is responsible for the physical transmission of data through the Internet. These not necessarily software protocols like the previous layers, but also hardware specifications, such as Ethernet, IEEE802.11 Wifi, [IPoAC](https://en.wikipedia.org/wiki/IP_over_Avian_Carriers), RS-232 Serial.

## HTTP Servers

In today's task, we will be making an HTTP server that can only accept local connections. This means that the server is only able to respond to connections from the same device.

We will be making a simple API: Application Program Interface, that allows one program to talk to the server.

APIs are a predefined system of messages and responses that a client and server can talk to each other over.

Example:

-   Discord has an API service so you can make bots,
-   Spotify also has an API so you can create your own client to listen music from.

These APIs divide their messages into 4 types: Create, Request, Edit and Delete (CRUD).

The HTTP protocol defines 4 different request types that a program can send: POST, GET, PUT and DELETE. These 4 request types correspond to each letter of CRUD.

### POST

POST requests are used to create data in the server. Most forms on the internet, use POST requests to send the response back to the server.

### PUT

PUT requests edit data in the server.

### GET

GET requests request data to be sent from the server to the client. Accessing a webpage uses GET requests.

### DELETE

DELETE requests are used to delete data from the server.

Sometimes, we send a request that is invalid to the server. In these cases, the server will send back an error code. Other times, if we are successful we will get back different status codes:

| Status Code | Description                                                                                                           |
| ----------- | --------------------------------------------------------------------------------------------------------------------- |
| 200         | OK - The request has succeeded                                                                                        |
| 201         | Created - The request has been fulfilled and a new resource has been created                                          |
| 204         | No Content - The server has fulfilled the request but there is no response body                                       |
| 400         | Bad Request - The server could not understand the request due to invalid syntax                                       |
| 401         | Unauthorized - The client must authenticate itself to get the requested response                                      |
| 403         | Forbidden - The client does not have access rights to the content                                                     |
| 404         | Not Found - The server could not find the requested resource                                                          |
| 500         | Internal Server Error - The server encountered an unexpected condition that prevented it from fulfilling the request  |
| 502         | Bad Gateway - The server was acting as a gateway or proxy and received an invalid response from the upstream server   |
| 503         | Service Unavailable - The server is currently unable to handle the request due to a temporary overload or maintenance |

### Responses

When a server receives a request, it usually is either an instruction or a request for data. If it is an instruction, the server will execute the function and return a status code of 200. But, if the client expects data back, we need to format the data in a method that is easy to read. These methods are called markup languages notation. Examples include: XML: eXtensible Markup Language, YAML: YAML ain't Markup Language, CSV: Comma Separated Values and JSON: JavaScript Object Notation. These languages all wrap up data with a title/description in a standardised method.

In our web server, we will use JSON, which looks like this:

```json
{
    users: [{
        authUserId: 1,
        email: "example@gmail.com",
        nameFirst: "Hayden",
        nameLast: "Jacobs",
        handleStr: "haydenjacobs",
        password: "correcthorsebatterystaple",
    }],
    tokens: [{
        userId: 1,
        token: "SAMPLE-TOKEN"
    }, {
        userId: 2,
        token: "SAMPLE-TOKEN2"
    }],
    name: "TestJSON"
}
```

## Python Code
```python
from http.server import BaseHTTPRequestHandler, HTTPServer
import json, urlparse

class MyHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        if self.path == '/':
            self.send_response(200)
            self.send_header('Content-type', 'text/html')
            self.end_headers()
            self.wfile.write(b"Hello, world!")
        elif self.path == '/api/data':
            data = {'name': 'John', 'age': 30}
            self.send_response(200)
            self.send_header('Content-type', 'application/json')
            self.end_headers()
            self.wfile.write(json.dumps(data).encode('utf-8'))
        else:
            self.send_error(404)

    def do_POST(self):
        if self.path == '/':
            self.send_response(200)
            self.send_header('Content-type', 'text/html')
            self.end_headers()
            self.wfile.write(b"Hello, world!")

    def do_PUT(self):
        if self.path == '/':
            self.send_response(200)
            self.send_header('Content-type', 'text/html')
            self.end_headers()
            self.wfile.write(b"Hello, world!")
            
def run():
    PORT = 8000
    server_address = ('', PORT)
    httpd = HTTPServer(server_address, MyHandler)
    print(f"Server running on port {PORT}")
    httpd.serve_forever()

if __name__ == '__main__':
    run()
```

## Task
Using the sample code above, or otherwise, create a web server that allows you to access some of your work from this term via unique URLs or endpoints.

- Your server should be accessed via `localhost:8000`
- Each endpoint should return the output of only one task from this term
- You can encode any inputs in the endpoint URL.
- You do not need to abstract out each task into its own function, but this will help.