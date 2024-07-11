---
alias: JavaScript
tags: [cs]
Created: 2024-03-02T17:05:26+10:00
Modified: 2024-07-03T19:35:33+10:00
---
 
JavaScript often abbreviated as JS is a [[Programming]] language used in [[Computer Science]] and core technology of the [[World Wide Web]], alongside [[HTML]] and [[CSS]]. 
## Variables
Javascript uses the keywords `var`, `let` and `const` to declare variables. Below are the rules:
1. Always declare variables
2. Always use `const` if the value should not be changed
3. Only use `let` if you can't use `const`
4. Only use `var` if you must support older browsers (pre 2015)
### Let
Variables declared with`let` have block scope and must be declared before use but cannot be redeclared in the same scope.
E.g.
```js
let x = "Asha";

let x = 5; // ILLEGAL
```
### Var
Variables declared with `var` have global scope and can be redeclared
```js
var x = "Asha";

var x = 0; // LEGAL
```
### Const
Variables defined with `const` must be assigned and cannot be reassigned
```js
const PI; // ILLEGAL
const PI = 3.14159; // LEGAL
PI = 3.14; // ILLEGAL
PI = PI + 10; // ILLEGAL
```
## Scope
### Block Scope
Variables declared inside a { } block cannot be accessed from outside the block unless declared with `var`:
```js
var y = 10; 
// Here y is 10
let x = 15; 
// Here x is 15
{
	let x = 2; // accessed within block
	var y = 5; // accessed globally
	// Here y is 5
	// Here x is 2
}
// Here x cannot be redeclared and is 15
// Here y can be used and is 5 
```
## Operators & Precedence
| Operator | Description | Val |
| ---- | ---- | ---- |
| == | equal to | 8 |
| === | equal value and equal type | 8 |
| != | not equal | 8 |
| !== | not equal value or not equal type | 8 |
| `typeof()` | returns the type | 14 |
| `instanceof()` | returns true if an object is an instance of an object type |  |
| & | Bitwise AND | 7 |
| \| | Bitwise OR | 5 |
| ~, ! | Bitwise NOT, Logical NOT | 14 |
| <<, >>, >>> | left shift, right shift, unsigned right shift | 10 |
| ! | NOT | 14 |
| +, - | Addition, Subtraction | 11 |
| ** |  | 13 |
| *, /, % | Multiplication, Division, Modulus | 12 |
| <, >, <=, >= | Less than, Greater than, Less than or equal, Greater than or equal | 9 |
| ^ | Bitwise XOR | 6 |
| && | Logical AND | 4 |
| \|\|  | Logical OR | 3 |
Full list: https://www.w3schools.com/js/js_precedence.asp
## Strings 
Strings in JS are immutable. They can be surrounded by either single quotation marks (' ') or double quotation marks (" " ). 
```js
let hamlet = "To be or not to be";
let macbeth = 'Tomorrow and tomorrow and tomorrow'
```

## Functions
A JS function is a block of code designed to perform a particular task.
```js
function name(p1, p2){
	// Code to be executed
}
```
### Declaring Variables via Functions
Functions in JS are fundamentally values, they can be assigned to an identifier through assignment statement or operate directly through a function declaration. The key differences are:
 - The function via assignment statement needs to be defined before the identifier is used
 - The function declaration is hoisted by the system to the top of the scope, so we may place the declaration anywhere in the file and use it
 E.g.
```js
let cube = function(x){
	return x * x * x;
}

console.log(quartic(2)); // LEGAL
console.log(cube(3));    // LEGAL
console.log(square(12)); // ILLEGAL

let square = function(x){
	return x * x;
}

function quartic(x){
	return x * x * x * x;
}
```
More examples using const:
```js
{
	const cube = function(x){
		return x * x * x;
	}
	console.log(quartic(2)); // LEGAL
	console.log(cube(3));    // LEGAL

	function quartic(x){
		return x * x * x * x;
	}
}
console.log(quartic(3)); // LEGAL
console.log(cube(4))     // ILLEGAL
```
### Arrow and Anonymous Functions
An alternative way to declare functions is without a function name and assigning it an identifier, as shown below:
```js
const name = function(parameters){
	// statements
}
```
We can now simplify our declaration to get an *arrow* function.
```js
const name = (parameters) => {
	// statements
}
```
We don't even need the curly braces.
```js
const name = (parameters) => expression // expression is single statement
```
## Objects
JS has several ways of dealing with objects. Typically done using a constructor function which sets the properties of the object, including the methods. Although as with arrays and strings, properties can be accessed using the '.' notation or using a 'key'.
E.g.
```js
// JSON format
let asha = {
	name: "Asha",
	age: 21
}
```
Equivalently: Object constructor with method property
```js
function person(name, age){
	this.name = name;
	this.age = age;
	this.toString = function() {
		return "<" + this.name + "," + this.age + ">"
	};
}
```
To declare and access the properties of an object:
```js
console.log(asha); // Returns { name: 'Asha', age: 21}
console.log(asha.name) // Returns Asha
console.log(asha["age"]); // Returns 21

asha.gender = "Male";
console.log(asha); // Returns { name: 'Asha', age: 21, gender: male}
```
Equivalently using a function with constructor:
```js
console.log(person.toString); // Returns [Function: toString]

let asha = new person("Asha", 21);
const bob = new person("Bob", 15);

console.log(asha); // Returns: person {name: "Asha", age: 21, toString: [Function]}
console.log(asha.toString()); // Returns <Asha, 21>
```
## Array
Using an array literal is the easiest way to create a JS array.
```js
const array_name = [item1, item2, ...];
```
### Adding elements
To add a new element to an array, use either `push()` method or `length()` property:
```js
const fruits = ["Banana", "Oranage", "Apple"];
fruits.push("Lemon"); // Adds Lemon returns new length
// Alternative
fruits[fruits.length] = "Lemon";
```
### Removing elements
To remove the last element of an array, use the `pop()` method:
```js
const fruits = ["Banana", "Oranage", "Apple"];
fruits.pop(); // Removes Apple, returns Apple
```
### Map
The `map()` function creates a new array populated with the results of calling a provided function on every element in the calling array. Here we show how to use map to double every element in an array:
```js
const array1 = [1, 4, 5, 8, 24];

const array2 = array1.map(x => x * 2);
// array2 = [2, 8, 10, 16, 48]
```
### Filter
The `filter()` method creates a new array with all elements that pass the test implemented by the provided function. Here is a test to filter the array down to characters with a length of 6+:
```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);
// result = exuberant", "destruction", "present"
```
### Reduce 
The `reduce()` method executes a reducer function on each element of the array, resulting in a single output value. The second parameter of the reduce method is an initial value for the 'accumulator'.
```js
const array1 = [1, 2, 3, 4];

const reducer = (accumulator, currentValue) => accumulator + currentValue;  
// 1 + 2 + 3 + 4  
console.log(array1.reduce(reducer));  
// expected output: 10  
// 5 + 1 + 2 + 3 + 4  
console.log(array1.reduce(reducer, 5));  
// expected output: 15
```
### Array Methods and Properties list
To see a full list of array methods see, https://www.w3schools.com/jsref/jsref_obj_array.asp


### Map

