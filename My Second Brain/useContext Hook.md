---
tags: [webdev]
Created: 2024-03-17T20:01:16+10:00
Modified: 2024-07-03T19:27:15+10:00
---
`useContext` is a react [[Hooks|Hook]] that lets you read and subscribe to context from your [[React Components|Component]]. Using it requires 3 simple steps: creating the context, providing the context and consuming the context.

### Creating the context
The built-in factory function `createContext(default)` creates a context instance:
```javascript
import {createContext} from 'react';

export const Context = createContext('Default Value');
```
The factory function accepts one optional argument: the default value.

### Providing the context
`Context.Provider`component available on the context instance is used to provide the context to its child components, no matter how deep they are.

To set the value of context use the `value` prop available on the `<Context.Provider value={value} />`:
```js
function Main(){
	const value = "My context value";
	return (
		<Context.Provider value={value}>
			<MyComponent/>
		</Context.Provider>
	);
}
```
Again, what's important here is that all the components that'd like later to consume the context have to be wrapped inside the provider component.

If you want to change the context value, simply update the `value` prop.

### Consuming the context
Consuming the context can be performed in 2 ways.
First is with the use of the `useContext(Context)` react hook:
```js
function MyComponent(){
	const value = useContext(Context);
	return <span>{value}</span>;
}
```
The hook returns the value of the context: `value = useContext(Context)`. The hook also makes sure to re-render the component when the context value changes.

The second way is by using a render function supplied as a child to `Context.Consumer` special component available on the context instance:
```js
function MyComponent() {  
	return (
		<Context.Consumer>
			{value => <span>{value}</span>}
		</Context.Consume>
	);
```

### The Issue
State should be held by the highest parent component in the stack that requires access to the state. To illustrate, we have many nested components. The component at the top and bottom of the stack need access to the state. To do this without Context, we will need to pass the state as `props` through each nested component. This is called "prop drilling"

```js
function Component1(){
	const [user, setUser] = useState("Asha S);

	return (
		<div>
			<h1>{'Hello ${user}!'} </h1>
			<Component2 user={user} />
		</div>
	);
}

function Component2({user}){
	return (
		<div>
		  <h1>Component 2</h1>
		  <Component3 user={user} />
		</div>
	);
}
...

function Component5({ user }) {
  return (
    <div>
      <h1>Component 5</h1>
      <h2>{'Hello ${user} again!'}</h2>
    </div>
  );
}
```
Even though components 2-n did not need the state, they had to pass the state along so that it could each component 5.

### Solution
The solution is to create context.
```js
const UserContext = createContext();

function Component1(){
	const [user, setUser] = useState("Asha S);

	return (
	    <UserContext.Provider value={user}>
	      <h1>{'Hello ${user}!'}</h1>
	      <Component2 />
	    </UserContext.Provider>
	  );
}

function Component2(){
	return (
		<>
		<h1> Component 2 </h1>
		<Component3/>
		</>
	);
}
...

function Component5(){
	const user = useContext(UserContext);

	return(
		<>
		<h1>Component 5</h1>
		<h2>{'Hello ${user} again'} </h2>
		</>
	);
}