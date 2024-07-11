---
tags: [webdev]
Created: 2024-03-17T20:02:15+10:00
Modified: 2024-07-03T19:35:32+10:00
---
The `useEffect` is a React [[Hooks|Hook]] that lets you synchronise a [[React Components|Component]] with an external system and perform side effects. Some examples of side effects are: fetching data, directly updating the DOM, and timers. `useEffect` accepts two arguments. The second argument is optional: `useEffect(<function>, <dependency>)`

## Dependency List
If you call `useEffect` without a dependency list, the function will be called every time the component is rendered (which is dangerous).
```js
useEffect(() => {
	// Runs on every render
});
```
If you call `useEffect` with an empty dependency list, the function will only be called when the component is first constructed:
```js
useEffect(() => {
	// Runs only on the first render
}, []);
```
If you call `useEffect` with a dependency list, the function will be called when the component is rendered if the list changed since the last render:
```js
useEffect(() => {
	// Runs on the first render
	// and any time any dependcy value changes
}, [prop, state]);
```
The list will often be filled with state variables and/or props. If a variable is in the dependency list and the effect function does not use that variable in some way, including it is probably a mistake. 

## Example
Use `setTimeout()` to count 1 second after initial render:
```js
function Timer(){
	const [count, setCount] = useState(0);

	useEffect(() => {
		setTimeout(() => {
			setCount((count) => count + 1);
		}, 1000);
	});

	return <h1> I've rendered {count} times! </h1>;
}
```
Bur wait! It keeps counting even thought it should only count once. `useEffect` runs on every render. That means that when the count changes, a render happens which then triggers another effect. This is not what we want and there are several ways to control when side effects run.

So to fix our initial issue, lets run this effect on the initial render.
```js
function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setTimeout(() => {
      setCount((count) => count + 1);
    }, 1000);
  }, []); // <- add empty brackets here

  return <h1>I've rendered {count} times!</h1>;
}
```
## Example with Fetch()
Below is an example that uses the weather app API to fetch data via a `useEffect`:
```js
const API_KEY = "";
const WEATHERAPI_REQUEST = 'https://api.weatherapi.com/v1/forecast.json?key={API_KEY}&...'

const [weather, setWeather] = useState(null);

useEffect(() =>{
	fetch(WEATHERAPI_REQUST)
	.then(res => res.json())
	.then(json => setWeather(json));
}, []);
```
