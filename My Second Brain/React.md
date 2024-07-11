---
tags: [webdev]
Created: 2024-03-06T12:09:13+10:00
Modified: 2024-07-03T19:35:33+10:00
---
 React is a free and open-sourced front-end [[JavaScript Programming|JavaScript]] library for building user interfaces based on components. It is maintained by Facebook or Meta and a community of individual developers and companies.

Here is a small example of a simple ReactJS program:
```javascript
import React, { useState } from 'react';
import login from '../auth.js';

const loginScreen = () => {
	const [username, setUsername] = useState('');
	const [password, setPassword] = useState('');
	
	const handleLogin = () => {
		login(username, password);
	};

	return (
		<div>c
			<form> 
			<label for="username"> Username: </label>
			<input
				type='text'
				name='username'
				value={username}
				onChange={e => setUsername(e.target.value)}
			/>

			<label for="password"> Password: </label>
			<input 
				type='password'
				name='password;
				value={password}
				onChange={e => setPassword(e.target.value)}
			/>

			<button type='button' onClick={handleLogin} /> 
			</form>
		</div>
	);
}
```
# React Native
React Native is an extension to React designed for developing mobile applications. React Native compiles to mobile specific native code allowing to build cross-platform mobile applications using only a single language.

# Fetch
We can simulate [[HTML#GET and POST Requests]] in JS using the `fetch()` function. The fetch request works by passing in the url for the data and an optional parameter containing headed data for the request being sent (i.e. authorisation tokens). Here is a simple fetch request using the `fetch()` method and some promises to simulate a GET request:
```js
fetch('https://jsonplaceholder.typicode.com/posts/1')
	.then(response => response.json())
	.then(json => console.log(JSON.stringify(json)))
```
Here is a simple fetch request using the `fetch()` method and some promises to simulate a POST request:
```js
const headerContent = {
  method: 'POST',
  body: JSON.stringify({
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  }
}

fetch('https://jsonplaceholder.typicode.com/posts', headerContent)
  .then(response => response.json())
  .then(json => console.log(json))
```

# Props 
React props work very similar to how arguments get passed into functions. When we want to pass props to a component we first need to pass that component to the `props` object. We can then define what props we want to pass when calling the component and use these props by their name in the component using `props.propName`. 

Here we create a `WelcomeUser` component that takes in the `props` object and uses the username thats passed in: 
```javascript
const WelcomeUser = (props) => {
	return (
		<div> 
			<h1> Welcome,{props.firstName}{props.lastName} </h1>
		</div>
	);
};

ReactDOM.render(
	<WelcomeUser firstname = 'Asha' lastName = 'Saunders' />,
	document.getElementByID('root');
);
```
We can also pass in an object as a prop and use its attribute names tied to the object to reference those values [[JSX|Example]].
