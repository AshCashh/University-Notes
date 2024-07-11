---
tags: [cs]
Created: 2024-04-16T17:23:28+10:00
Modified: 2024-07-03T19:35:33+10:00
---
JSON (JavaScrip Object Notation) is an open standard file format and data interchange format that uses human-readable text to store and transmit data objects consisting of attribute value pairs and arrays. It is a commonly used data format with diverse uses in electronic data interchange, including that of [[Web Development|Web Applications]] with servers.

JSON is derived from [[JavaScript Programming|JavaScript]] but many modern [[Programming]] languages include code to generate and parse JSON-format data. JSON filenames use the extension `.json`. 

# Web Tokens
JWT is an open standard for securing information stored as a JSON object through transmission. We can use JWT tokens to authenticate a user upon login and use that token then to access API's behind authentication points. The overall structure of a JWT token is a chain of encoded character segments separated by dots. An example being `xxxxxx.yyyyyy.zzzzzz` with `x` being the head, `y` containing the information and `z` being a validation signature.

#### The Header
The header is a JSON object containing two pieces of important information:
1. The type of token
2. The algorithm used for the signature
```json
{
	"alg": "HS256",
	"typ": "JWT"
}
```
#### The Payload
The payload include all the information we want to transfer.
```json
{
	"email": "admin@mail.com",
	"exp": 158371382, // Expiration time
	"iat": 23983201  // Issued at time
}
```
#### The Signature
The signature is a secret key used to encode the token. The header and payload are put through a hashing algorithm encoded with the secret key. This allows us to ensure and verify that the token is genuine and valid.
### Using the Token
So how do we use our token? Before we can use the token we first need to obtain it. We can do this by sending a POST request to our API with a body containing our login information. This will return an authorisation token which we can then use.
```js
const bearer;

fetch("https://jsonplaceholder.typicode.com/users/login", {
	method: "POST",
	headers: {
		"Content-Type": "application/json",
	},
	body: JSON.stringify({
		email,
		password,
	})
}).then(res => res.json()).then(data => bearer = data.token);
```
We can now use it by passing it through the 'Authorization' header as such:
```json
{
 header:
	 Authorization: Bearer <token>
}
```
We can use this header as an additional parameter inside of our fetch request in Javascript like:
```js
fetch("https://jsonplaceholder.typicode.com/api/premium", {
	method: "GET",
	headers: {
		Authorization: `Bearer ${bearer}`
	}
}).then(res => res.json()).then(data => /*do something */ )
```

