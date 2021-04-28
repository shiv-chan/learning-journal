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

The server and the client could directly exchange, but most of the time there are numerous entities such as modem or routers between two. These computers are collectively called **proxy**.

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
- The rest is [HTTP headers](#http-headers) which includes an additional information such as host, authentication, caching, cookies or CORS.
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

In the HTTP response example...

- `HTTP/1.1` is the version of HTTP protocol.
- `200` is the status code which indicates if the request was successful or not and why.
- `OK` is the status message.
- the rest is [HTTP headers](#http-headers).
- (a body) the fetched resourses like HTML, CSS or image.

## HTTP headers

HTTP headers include an additional information attached to an HTTP request or an HTTP response.

There are four types of HTTP headers.

- General header

This can present in both request and response, and this doesn't affect any on the content itself.

e.g. Cache-Control

- Request header

This one is in an HTTP request and send the information about the request context.

The server can tailor the response based on this.

e.g. Authorization, CORS

- Request header

This one is in an HTTP response and doesn't relate to the content of the message. This is the information about the context of the response.

e.g. Age, Location, Server

- Entity header

This can present in both an HTTP request and response, and it describes the payload of an HTTP message.

e.g. Content-Length, Content-Language, Content-Encoding, Content-Type, Expires

### Accept

`Accept` lets the server know which the content type the client can understand.

The content types are expressed as MIME type, the following.

#### MIME type

MIME is an acronym of Multipurpose Internet Mail Extensions.

The syntax of MIME types:

| Syntax (type/subtype) | Description             |
| --------------------- | ----------------------- |
| text/plain            | Textual files (default) |
| text/html             | HTML format data        |
| text/css              | CSS format data         |
| text/javascript       | JavaScript format data  |
| image/jpeg            | jpeg format data        |
| video/mp4             | mp4 format data         |
| application/json      | JSON format data        |

### Content-Type

`Content-type` tells the client which the content type of the returned content actually is

### Authorization

`Authorization` contains the credentials to authenticate a user agent with a server.

HTTP can control the access or check the authentication.

### CORS (Cross-Origin Resource Sharing)

As it's mentioned above, HTTP has an access control.

XHR (XMLHttpRequest) and Fetch API are applied the same-origin policy as default which means an origin (protocol, host, port) where the user agent, mostly the Web browser, sends the request from should be the same as the server.

Otherwise, the server denies the request and return the outcome with its reason as the following.

Let's say making a fetch request from `https://www.learningjournal.com/login` to the server.

| URL                                                     | Outcome     | Reason             |
| ------------------------------------------------------- | ----------- | ------------------ |
| https://www.learningjournal.com/api/authentication      | Same origin |                    |
| https://api.learningjournal.com/authentication          | Failure     | Different host     |
| http://www.learningjournal.com/authentication           | Failure     | Different protocol |
| https://www.learningjournal.com:3000/api/authentication | Failure     | Different port     |

By adding HTTP headers in an HTTP response, the server can describe which origins are permitted to read the data or the information from a Web browser.

There are some ways to control the access, but the following are ones of them.

```
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
```

Assume that `https://hoge.other` tries to fetch the data from `https://foo.example`.

If the server sent this: `Access-Control-Allow-Origin: https://foo.example` or `Access-Control-Allow-Origin: *`, the resource can be accessed.

The former accepts the request only from `https://foo.example`, and the latter accepts the request from any origin.

#### Reference

- [An overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [What is TCP?](https://www.fortinet.com/resources/cyberglossary/tcp-ip)
- [Accept](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept)
- [Content-Type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [HTTP authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)
- [](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
