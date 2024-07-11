---
Created: 2024-03-10T15:08:25+10:00
Modified: 2024-07-03T19:35:33+10:00
---

## OLD xHttpRequest Callback Function
```js
let xHttpRequest = null;

const oldButton = document.getElementById("oldBtn");
oldButton.addEventListener('click', () => {
	// Adapted from the MDN AJAX examples
	//https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX/Getting_Started
	xHttpRequest = new XMLHttpRequest();

	if (!xHttpRequest) {
		console.log("Cannot create HTTP Request");
		return false;
	}
	xHttpRequest.onreadystatechange = processResponse;  
	xHttpRequest.open("GET", "https://reqres.in/api/unknown");  
	xHttpRequest.send();  
});
```