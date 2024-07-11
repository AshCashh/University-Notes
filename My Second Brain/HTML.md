---
tags: [webdev]
Created: 2024-03-03T14:59:34+10:00
Modified: 2024-07-03T19:35:33+10:00
---
HTML or HyperText Markup Language is the standard markup language for documents designed to be displayed in a web browser. It defines the content and structure of web content. It is often assisted by technologies such as [[CSS]] and scripting languages such as [[JavaScript Programming|JavaScript]]

Web browsers receive HTML documents from a web server or from local storage and render the documents into multimedia web pages. HTML describes the structure of a web page semantically.

# GET and POST Requests
When communicating with the web we can use the [[Hypertext Transfer Protocol|HTTP]] protocol to send requests. These can consist of retrieving data such as static webpages and web resources (GET requests) and sending data such as form data (POST requests). Once a request has been send the server will respond with a status report regarding the request. These reports will contain useful information such as the requested status code, request data and the server sending the status report.

Here is an example of a simple GET request from the Mozilla site:
```html
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: en-US
```
```html
HTTP/1.1 404 Not Found
Date: Tue, 15 Mar 2022 20:18:22 GMT
Server: Apache
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html...>
```
Here is an example of a simple POST request and response from the Mozilla site:
```html
POST /contact_form.php HTTP/1.1
Host: developer.mozilla.org
Content-Length: 64
Content-Type: application/json

{
  "Id": 12345,
  "Customer": "John Smith",
  "Quantity": 1,
  "Price": 10.00
}
```
```html
HTTP/1.1 200 OK
Content-Length: 19
Content-Type: application/json

{"success":"true"}
```
