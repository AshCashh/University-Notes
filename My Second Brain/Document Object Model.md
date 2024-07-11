---
Created: 2024-07-03T09:03:24+10:00
Modified: 2024-07-11T19:59:40+10:00
tags:
  - webdev
---

The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style and content. The DOM represents the document as nodes and objects; that way, [[Programming]] languages can interact with the page.

A web page is a document that can be either displayed in the browser window or as the [[HTML]] source. In both cases, it is the same document but the DOM representation allows it to be manipulated. As an object-oriented representation of the web page, it can be modified with a scripting language such as [[JavaScript Programming|JavaScript]]

Below is an example of how the DOM is structured:
```html
<html>
	<head>
		<title> My Blog </title>
	</head>
	<body>
		<h1> Blog #1 - My first blog </h1>
		<p> Yo Hello, It's Ash here is my first blog yo </p>
		<p> See my other articles <a href="#">here </a> </p>
	</body>
</html>
```
```
├── html
│   ├── head
│   │   ├── title
│   │   │   ├── "My Blog"
│   ├── body
│   │   ├── h1
│   │   │   ├── "Blog #1 - My first blog"
│   │   ├── p
│   │   │   ├── "Yo Hello, It's Ash here is my first blog yo"
│   │   ├── p
│   │   │   ├── "See my other articles"
│   │   │   │    ├── a
│   │   │   │    │   ├── "here"
```
We can also interact with the DOM and its elements using javascript commands. Here are a few example commands and what they do:

| Access Methods                                 | Definition                                                                  |
| ---------------------------------------------- | --------------------------------------------------------------------------- |
| `document.getElementById("main")`              | Returns the element with id="main" and null otherwise                       |
| `document.getElementByTagName("p")`            | Returns an array of all "p" tag elements from the document                  |
| `document.getElementsByClassName("highlight")` | Returns an array of all elements with class = "highlight" from the document |
| `document.querySelectorAll("div > p")`         | Returns an array of all elements matching the CSS sector "div > p"          |
