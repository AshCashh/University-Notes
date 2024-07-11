---
tags: [webdev]
Created: 2024-04-21T12:24:15+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Express is an application framework designed for [[Node.js]]. To use Express we must first install it using `npm install express -g`. Let's take a look at a simple hello world express program:
```javascript
const express = require("express");
const app = express();

const hostname = "127.0.0.1";
const port = 3000;

// any get request that comes in from the root downwards is handled here
app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Express app listening at http://${hostname}:${port}/`);
});
```
We can handle routing using the `Router` class:
```javascript
const express = require("express");
const router = express.Router();

// define the home page route
router.get("/", (req, res) => {
  res.send("Home page");
});

// This route path will match requests to /about
router.get("/about", (req, res) => {
  res.send("About page");
});

module.exports = router;
```
## Express Generator
Express generate will create and setup a lot of the necessary boilerplate for an express application. To use it we must install it using `npm install express-generator -g` and then we can create an Express application using `express helloworld`.

# Express Middleware
Middleware functions are special functions which have access to:
- The request object - `req`
- The response object - `res`
- The next middleware function in the cycle - `next`
The `next` function passes control to the next middleware. If we don't want to continue the chain we simply don't call `next()` at the end of our middleware function.

Middleware functions can be passed in through a couple different methods:
- The middleware function itself
- A series of middleware functions separated by a comma
- An array of middleware functions
```javascript
const express = require("express");
const app = express();
const port = 3000;

// looking at request and logging
const logOriginalUrl = (req, res, next) => {
	console.log('Request URL: ${req.originalUrl}');
	next();
};

const logMethod = (req, res, next) => {
  console.log(`Request Type: ${req.method}`);
    next();
};
// chaining middleware functions
const middlewareFunctions = [logOriginalUrl, logMethod];

app.get("/user/:id", middlewareFunctions, (req, res, next) => {
  res.send(`User: ${req.params.id}`);
});

app.listen(port, () => {
  console.log(`Example app listening on port: ${port}`);
});
```
Result: 
```
$ node app.js
Example app listening on port: 3000
Request URL: /user/12344
Request Type: GET
```
Here the parameter is handled and the Request URL and Request Type are logged. The key is the call to `next()`, which means that these are executed in turn.

### Newer Version
App.js:
```javascript
const express = require("express");
const app = express();
const port = 3000;
const indexRouter = require('./index');
const docRouter = require('./docs');

...
// same logOriginalUrl logMethod functions
...
const middlewareFunctions = [logOriginalUrl, logMethod];

app.use('/', middlewareFunctions, indexRouter);
app.use('/docs', middlewareFunctions, docRouter);

app.listen(port, () => {
  console.log(`Example app listening on port: ${port}`);
});
```
Index.js:
```javascript
const express = require('express');
const router = express.Router();

router.use((req, res, next) => {
	console.log(new Date()); // Router specific logging
	next();
})
// GET home page.
router.get('/', (req, res, next){
	res.send("<h1> Home Page router </h1>);
});

router.get('/user/:id', (req, res, next){
	res.send(`User: ${req.params.id}');
});
module.exports = router;
```
Result: 
```
$ node app.js
Example app listening on port: 3000
Request URL: /
Request Type: GET
2024-04-21T14:47:44.8132
Request URL: /user/12555
Request Type: GET
2024-04-21T14:47:44.8132
```
# Knex
Knex is a SQL query builder for node and express. It helps to manage connectivity and connection pooling. Whenever we initialise a new app we need to create/edit the `knexfile.js` to include all the needed and required information for our database.
```js
module.exports = {
  client: "mysql",
  connection: {
    host: "127.0.0.1",
    database: "myScheme",
    user: "root",
    password: "",
  },
};
```
```js
router.get("/api/city", (req, res, next) => {
  req.db
    .from("city")
    .select("name", "district")
    .then((rows) => {
      res.json({ Error: false, Message: "Success", City: rows });
    })
    .catch((err) => {
      console.log(err);
      res.json({ Error: true, Message: "Error in MySQL query" });
    });
});
```
# Helmet 
Helmet is a collection of security middlewares that sets headers and allows us to avoid some common vulnerabilities,
```js
const express = require("express");
const helmet = require("helmet");

const app = express();

app.use(helmet());
```

# Using HTTPS
Making Express use HTTPS is as simple as passing in the certificate files when starting the server.
```ts
const fs = require("fs");
const https = require("https");
const privateKey = fs.readFileSync("sslcert/server.key", "utf8");
const certificate = fs.readFileSync("sslcert/server.crt", "utf8");

const credentials = { key: privateKey, cert: certificate };
const express = require("express");
const app = express();

// Express configuration goes here

const server = https.createServer(credentials, app);
server.listen(443);
```