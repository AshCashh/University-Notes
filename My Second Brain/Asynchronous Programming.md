---
aliases:
  - Asynchrony
  - Asynchronous
tags:
  - webdev
  - cs
Created: 2024-03-10T14:53:15+10:00
Modified: 2024-07-10T18:43:48+10:00
---
Asynchronous programming also known as Asynchrony in [[Programming]] refers to the occurrence of events independent of the main program flow and ways to deal with such events. It is a technique that enables programs to start a potentially long-running task and still be able to be responsive to other events while that task runs.

Since [[JavaScript Programming|JavaScript]] is a synchronous programming language, operations are stacked in order of execution and while each operation is being processed nothing else can happen. This is a major problem when dealing with websites and applications as we may need to request some data from an [[Application Programming Interface|API]] while running some other tasks. However, there are some approaches that allow asynchrony within JS, these consist of: Callback functions, Promises and Async and Await.
# Callback Functions
Callback functions are essentially functions that are passed in as arguments to be executed at some other later time. For example, lets say on our HTML page we have a button: `<button id='callback-btn'> Click Here </button>`. And in our JS file we have an event listening waiting for that button to be pressed. When the button gets pressed we callback to a function that simply prints to the console 'Button Pressed'.
```js
document.queryselector('#callback-btn')
	.addEventListener('click', () => {
		console.log('Button Pressed');
});
```
So as we can see, `.addEventListener()`. is taking 2 parameters, the event listener type 'click' and the second being the callback function.

An older use of callback functions can be seen [[JS Code Snippets#OLD xHttpRequest Callback Function|here]] using an old style AJAX.

# Promises
Promises work by chaining functions from each other using the keyword `.then()`. We can also use `.catch()` at the end of our chain to throwback any errors we may retrieve. For example, let's say we want to print to the console the return data if and only if the fetch request returns a valid response, without having to freeze our application waiting for the API callback. We can use promises for this.
```js
fetch('https://jsonplaceholder.typicode.com/posts/1')
	.then((response) => {
		if (response.ok) {
			return response.json();
		}
		throw new Error('Failed network response');
	})
	.then((result) => {console.log(result)})
	.catch((error) => console.log('Problem with error message: ${error}'));
```

# Async/Await
We can also use async/await to accomplish the same thing:
```js
{
	() => {
		try{
			const response = await fetch('https://jsonplaceholder.typicode.com/posts/1')

			if (!response.ok){
				throw new Error('Failed network response');
			}

			console.log(await response.jason());
		} catch (error){
			console.log('Problem with error message: ${error});
		}
	}
}
```
