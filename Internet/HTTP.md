# What is HTTP?

HTTP is an acronym of HyperText Transfer Protocol.

It is a client-server protocol which exchanges any data on the Web between servers and clients.

## HTTP flow

1. Open a TCP
   > The Transmission Control Protocol (TCP) is a communications standard that enables application programs and computing devices to exchange messages over a network. It is designed to send packets across the internet and ensure the successful delivery of data and messages over networks.
2. Send HTTP request
   HTTP request is the message sent by the client, most of the time it is a Web browser.
   > The browser is always the entity initiating the request. It is never the server (though some mechanisms have been added over the years to simulate server-initiated messages).
3. Receive HTTP response
   HTTP response is the message sent by the server.
4. Close a TCP or resume the connection for further requests.

The server and the client could directly exchange, but most of the time there are numerous entities such as modem or routers between two.  These computers are collectively called **proxy**. 

## HTTP request

```
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```

In the HTTP request example...

- `GET` is an HTTP method. This could also be `POST`, `PUT`, `DELETE`.
- `/` is a path where to send the HTTP request. This is URL without the protcol (http://), the domain, or the TCP port.
- `HTTP/1.1` is the version of HTTP protocol.
- The rest is a HTTP header which includes an additional information such as host, authentication, caching, cookies or CORS.
- (a body) contain the resourse includes information like name or email address that are sent to the server with POST method.

## HTTP response

```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html... (here comes the 29769 bytes of the requested web page)
```

- `HTTP/1.1` is the version of HTTP protocol.
- `200` is the status code which indicates if the request was successful or not and why.
- `OK` is the status message.
- the rest is HTTP headers.
- (a body) the fetched resourses like HTML, CSS or image.



#### Reference

- [An overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [What is TCP?](https://www.fortinet.com/resources/cyberglossary/tcp-ip)