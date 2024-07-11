---
tags: [webdev]
Created: 2024-03-09T20:45:22+10:00
Modified: 2024-07-03T19:35:33+10:00
---
JSX or Javascript XML is a [[React]]-specific syntax that allows for [[HTML]] code to coexist inside of [[JavaScript Programming|JavaScript]] code. In the example below we can see `<h1>` tags nested into JS code as well as JS variables embedded into HTML code. It's important to remember when we return JSX code we must only return a single value. This is why everything returned gets surrounded in a `<div>` tag.
```javascript
const user = {
	firstName: 'Asha',
	lastName: 'Saunders'
};

const formatName = (user) => {
	return '${user.firstName} ${user.lastName}';
};

const WelcomeUser = (props) => {
	return (
		<div>
			<h1> Welcome, {formatName(props.user)} </h1>
		</div>
	);
};

ReactDOM.render(
	<WelcomeUser {...user} />,
	document.getElementByID('root')
);
```