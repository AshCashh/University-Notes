---
tags: [webdev]
Created: 2024-03-12T19:14:56+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Functions starting with `use` are called Hooks. `useState` is a built-in Hook provided by [[React]]. Hooks are more restrictive than other functions. You can only call hooks at the top of your [[React Components|Components]] (or other Hooks). If you want to use `useState` in a conditional or a loop, extract a new component and put it there.

We can do the same thing as [[React Components#Component State|Here]] using function based components but using Hooks to manage its state. To create a state variable we first must declare the variable along with a function to alter the variable and tie them both together using `useState`. 
```js
import React, {useState} from 'react'; // Imports useState
const App = () => {
	// Here we say
	// - count: this is our state variable
	// - setCount: we use this to change the value of our state variable
	// - useState(0): use to set the initial value for state variable
	const [count, setCount] = useState(0);

	useEffect(() => {
		document.title = 'You clicked ${count} times';
	});

	return (
		<div className="App">
			<h1> Total count is: {count} </h1>
			<button onClick={() => setCount(count + 1)}>
				Press me to increase count
			</button>
		</div>
	);
}
```
# React Hooks
- [[useContext Hook]]
- [[useEffect Hook]]
- 
