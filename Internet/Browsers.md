# Browsers

## What is a browser?

> A web browser is application software for accessing the World Wide Web.

Most popular web browsers include Google Chrome, Mozilla Firefox, Microsoft Edge, and Apple Safari.

It retrieves the information from other parts of the web and displays on your device.

## How a browser works?

The following steps show how a browser works exactly.

When you type a web address into your browser...

1. The browser asks the computer if it can recognizes the IP address based on the web address(strictly speaking, the domain name). If it can, go to the next step. If not, the browser goes to DNS server and find the IP address.
2. Once it gets IP address, it sends HTTP request message to the server asking it to send back a copy of the website to the client.
3. If the server accepts the request, it starts to send the website's file to the browser.
At this moment, the server breaks all data into small pieces which are called packets.
4. To display the website, the browser reassembles the packets in the original order.
Ta-da! you can now see the website!

#### Reference

- [What is a web browser?](https://www.mozilla.org/en-US/firefox/browsers/what-is-a-browser/)
- [Web browser](https://en.wikipedia.org/wiki/Web_browser)
- [How the Web works](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works)