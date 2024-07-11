---
tags: [webdev]
Created: 2024-04-15T19:49:39+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Node.js is a cross-platform, open source [[JavaScript Programming|JavaScript]] runtime environment that can run on Windows, Linux, Unix, macOS and more. Node.js runs on the V8 JS engine and executes JS code outside a web browsers. Node.js lets developers use JS to write command line tools and for server-side scripting.

Node.js is server side JS used to support rapid server connections and processing. Let's create a simple hello world web server in Node.js
```javascript
const http = require("http");

const hostname = "127.0.0.1";
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Hello World\n");
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

