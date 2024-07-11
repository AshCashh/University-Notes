---
as: Python
tags: [cs]
Created: 2024-02-27T19:55:51+10:00
Modified: 2024-07-03T19:35:33+10:00
---
 
Python is a high-level general-purpose [[Programming]] language used in [[Computer Science]]. Its design philosophy emphasises code readability with the use of significant indentation.

Python is dynamically typed and garbage-collected. It supports multiple programming paradigms including structured, object oriented and functional programming.

# Variables
Python has no command for declaring a variable. A variable is created the moment you first assign a value to it.
```python
x = 5      # x is of type int
y = "Ash"  # y is of type str
```
Python allows you to assign values to multiple variables in one line:
```python
x, y, z = "Orange", "Banana", "Cherry"
```

## Casting
If you want to specify the data type of a variable, this can be done with casting.
```python
x = str(3)   # x will be '3'
y = int(3)   # y will be 3
z = float(3) # z will be 3.0
```
## Multi Word Variable Names
Variable names with more than one word can be difficult to read.
There are several techniques you can use to make them more readable:
### Camel Case
Each word, except the first starts with a capital letter:
```python
myVariableName = "Ash"
```
### Pascal Case
Each word starts with a capital letter:
```python
MyVariableName = "Ash"
```
### Snake Case
Each word is separated by an underscore character:
```python
my_variable_name = "Ash"
```

## Data Types
Python has the following data types built-in by default:

| Type            | Name                             | Example                               |
| --------------- | -------------------------------- | ------------------------------------- |
| Text Type       | `str`                            | `x = "Hello World"`                   |
| Numeric Types:  | `int`,`float`,`complex`          | `x = 20`,`20.5`, `1j`                 |
| Sequence Types: | `list`,`tuple`,`range`           | `x = ["apple"], ("apple), range(6)`   |
| Mapping Type:   | `dict`                           | `x = {"name" : "Ash", "age" : 21}`    |
| Set Types:      | `set`,`frozenset`                | `x = {"apple"}, frozenset({"apple"})` |
| Boolean Type:   | `bool`                           | `x = True`                                      |
| Binary Types:   | `bytes`,`bytearray`,`memoryview` | `x = b"Hello", bytearray(5), memoryview(bytes(5))`                                      |
| None Type:      | `NoneType`                       | `x = None`                                      |
### Get the Type
You can get the data type of a variable with `type()` function

## Strings
String in python are surrounded by either single quotation marks (' ') or double quotation marks (" " ). 
```python
print("Hello")  
print('Hello')
```
### Multiline Strings
You can assign a multiline string to a variable by using three quotes:
```python
a = """Lorem ipsum dolor sit amet,  
consectetur adipiscing elit,  
sed do eiusmod tempor incididunt  
ut labore et dolore magna aliqua."""  
print(a)
```
### Strings are Arrays
Like many other popular programming languages, strings in Python are arrays of bytes representing unicode characters.

However, Python does not have a character data type, a single character is simply a string with a length of 1.

Square brackets can be used to access elements of the string.
```python
a = "Hello, World!"  
print(a[1])
```
### Looping through a String
Since strings are arrays, we can loop through the characters in a string with a `for` loop:
```python
for x in "banana":
	print(x)
	```

### String Length
To get the length of a string, use the `len()` function.
```python
a = "Hello, World!"  
print(len(a)) # returns 13
```

### Slicing Strings
You can return a range of characters by using the slice syntax.
Specify the start index and the end index, separated by a colon, to return a part of the string.
```python
b = "Hello, World!"
print(b[2:5]) # returns llo
```

### Modify Strings
Below are the more common built-in methods you can use on strings.
Learn more here: https://www.w3schools.com/python/python_ref_string.asp

| Method            | Function Declaration | Example `a = "Hello, World!"`                  |
| ----------------- | -------------------- | ---------------------------------------------- |
| Upper Case        | `upper()`            | `a.upper()` Returns: `HELLO, WORLD!`           |
| Lower Case        | `lower()`            | `a.lower()` Returns: `hello, world!`           |
| Remove Whitespace | `strip()`            | `b = " Ello "` Returns: `Ello`                 |
| Replace String    | `replace()`          | `a.replace("H", "J")` Returns:  `Jello World!` |
| Split String      | `split()`                     | `a.split(",")` Returns: `['Hello', 'World!']                                               |

## Math
Python allows many mathematical functions using the `math` module
```python
import math
```
Further functions can be found here: https://docs.python.org/3/library/math.html
Or here: https://www.w3schools.com/python/module_math.asp

### Math Methods
| Method         | Description                                  | Function Declaration        | Example                               |
| -------------- | -------------------------------------------- | --------------------------- | ------------------------------------- |
| Exponentiation | Returns the value of $x$ to the power of $y$ | `**`, `pow()`, `math.pow()` | `x**y`, `pow(x, y)`, `math.pow(x, y)` |
| Square Root    | Returns the square root of a number                                             | `math.sqrt()`                            | `math.sqrt(x)`                                      |
| Natural Exponential               | Returns $e$ raised to the power of $x$                                             | `math.exp()`                            | `math.exp(x)`                                      |
| Logarithm               | Returns the logarithm of $x$ with $y$ as the base                                             | `math.log()`, `math.log10()`, `math.log2()`                            | `math.log(x, y)`, `math.log10(2)`                                      |

# Tuple
```python
t=(1,2)  # tupple literal
t[0]     # accessing item = 1
t[0] = 1 # cant modify a tuple
```

# [[Regular Language#Languages|Languages]]
While Python provides us a datatype for strings, these are generally only intended for Unicode characters. For strings over arbitrary elements we can use tuples. Programmatically, languages are usually dealt with by building a parser, rather than sets of strings. However, the mathematical definitions can still be implemented.

$$\forall v\in V\exists r\in R:r\cancel{\in} v\land(p\in v:p\cancel{\in}C)$$