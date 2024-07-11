---
aliases:
  - Component
  - Components
tags: [webdev]
Created: 2024-03-12T18:44:25+10:00
Modified: 2024-07-03T19:35:33+10:00
---
[[React]] components are reusable sections of code that work similar to functions but are used to create elements which can be used, generally for the front end.

Here is an example of a React component that displays a welcome message to the user
```javascript
const user = [
	firstName: 'Asha',
	lastName: 'Saunders'
];

const WelcomeUser = () => {
	return (
		<div> 
			<h1> Welcome, {user.firstName} {user.lastName} </h1>
		</div>
	);
};

ReactDOM.render(
	<WelcomeUser />,
	document.getElementById('root')
);
```
### Class-Based Components
When can create components using either classes or functions. Classes were how components were originally made however with new updates we can now create components using functions. Below is an example of how to create a function using classes.
```js
class App extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div className="App">
        <h1>Hello World!</h1>
      </div>
    );
  }
}
// Adding internal state via constructor
class Golden extends React.Component {
	constructor(props){
		super(props);
		this.state = {...props};
	}
	render(){
		return (
			<div className = "Golden">
				<h2> Name is: {this.state.name} </h2>
				<h2> Age is: {this.state.age} </h2>
			</div>
		);
	}
}
```
### Function-Based Components 
Function based components can be created using either the `function` keyword or trying an anonymous function to a variable.
```js
// Simple function
function DisplayName(props){
	return (
		<h1> My name is {props.name} </h1>
	)
}
// More complex
function App(){
	return (
		<div className="App">
			<h1> Hello World </h1>
			<h2> Second paragraph </h2>
		</div>
	);
}
```
### Component State
There are a few ways we can modify the state of our components and these depend on how we define our components. To create and modify the state of a class based component we first need to create a constructor for our class and create our state variables there. We can then alter the state of these variables using the `setState()` method.
```js
class App extends React.Component{
	constructor(propers){
		super(props);
		this.state = {
			// Here we define a state variable 'count'
			// and assign its starting value to 0
			count: 0;
		}
	}
	render(){
		return (
		<div className="App">
			<h1> Total count is: {this.state.count} </h1>
			<button onClick={() => this.setState({count:this.state.count+1})}>
			Click me
			</button>
		</div>
		);
	}
}
```
# Component Lifestyle
![[Pasted image 20240312184821.png|centre|300]]
