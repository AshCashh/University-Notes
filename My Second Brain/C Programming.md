#cs
C is a programming language used in [[Computer Science]], developed in the early 1970s by Dennis Richie. C is a compiled language, meaning that a separate program is used to efficiently translate the source code into [[Assembly Programming|Assembly]]. It's compilers are capable of targeting a wide variety of [[Microprocessors & Microcontrollers|Microprocessor]] architectures and hence it is used to implement all major operating system kernels. Compared to many other languages, C is very efficient programming language as it constructs map directly onto machine [[Instructions]].

[[C Programming#Pointers]]
[[C Programming#Addressing]]



## Main Function
C is a procedural language and hence all code subsides in a procedure (known as function). In C, the main function is the entry point to the program. Program execution will generally begin in this function, where we can make calls to other functions.
```c
int main()
{
	// Function body
	return 0;
}
```
The purpose of returning a zero at the end of the main function is to signify the exit status code of the process. An exit status of 0 is traditionally used to indicated sucess, while all non-zero values indicate failure.

## Statements
C programs are made up of statements. Statements are placed within scopes (indicated by braces ({})) and are executed in the order they are placed. All statements in C must terminate with a semicolon (;). Although assembly instructions translate to a single OPCODE, a single C statement can translate to multiple OPCODEs.
```c
int main()
{
	int x = 3;
	{
		int y = 4;
		x = x + y;
	}
	// x is now 7
	// y is no longer in scope
	return 0;
}
```
## Comments
C supports two styles of comments. The first of these are known as "C-style comments", which allow mult-line/block comments. Multi-line comments use:
```c
/*
	This is a multi-line comment.
*/
```
The second style is known as "C++ style comments", which allow single-line comments. These comments are denoted by the // syntax

## Variables
Variables are used to temporarily store values in memory. Variables have a type and a name and must be declared before use.

### Declaration
To declare a variable in C, we must specify the type and name of that variable.
```c
int x;
```
This variable can then be assigned to using the = operator.
```c
x = 4;
```
## Initialisation
To optionally assign a value during declaration, we can apply the assignment operator after the declaration. This is known as a variable initialisation, as we are assigning an initial value to the variable.
```c
int x = 4;
```
Note that using uninitialised variables results in unspecified behaviour in C, meaning that the value of such variables in unpredictable.

## Types
While AVR assembly supports 8-bit registers, C supports larger data types by treating them as a sequence of bytes. We can also create compound data types with struct and union.

### Type Specifiers
Type specifiers in declaration define the type of the variable. The signed char, signed int and signed short int, signed long int types, together with their unsigned variants and enum, are all known as integral types. float, double and long double are known as floating or floating-point types. The following table summarises various numeric types in C:
![Pasted image 20230324123646.png](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230324123646.png?1679625406838)
### Type Qualifiers 
Types can be qualified with additional keywords to modify the properties of the identifier. Three common qualifers are const, static and volatile.
- const - indicates that the variable is constant and cannot be modified.
- static - indicates that the variable has a global lifetime
- volatile - indicates that the variable can be modified or accessed by other programs or hardware

### Portable Types
C has a set of standard types that are defined in the language specification, however the type specifiers shown above may have different storage sizes depending on the platform. Although this may be insigniicant for most platforms, microcontrollers use specific sizes for registers, meaning it is important to refer to the correct type specifiers when declaring a variable.

### Exact Width Types
The standard integers (stdint.h) library provides exact-width type definitions that are specific to the development platform. This ensures that variables can be initialised with the correct size on any platform
```c
#include <stdint.h>
int8_t i8; 
int16_t i16; 
int32_t i32; 
int64_t i64; 

uint8_t ui8; 
uint16_t ui16; 
uint32_t ui32; 
uint64_t ui64;
```
### Floating-Point Types
The float and double types can store floating-point value types in C. Their implementation allows for variable levels of precision, i.e., extremely large and extremely small values. These types are very useful on systems with a floating point unit (FPU) or equivalent.
As the ATtiny1626 does not have an FPU, arithmetic involving floating point values is highly inefficient. Therefore, integer arithmetic should be utilised when possible. Note that a single floating point number or operation causes the entire floating point library to be included which can require a large amount of memory.

## Literals
Literals are used when specific values need to be specified directly in a program

## Integer Prefixes
Integer literals are assumed to be base 10 unless a prefix is specified. C supports all of the following prefixes:
- Binary (base 2) - 0b
- Octal (base 8) - 0
- Decimal (base 10) - no prefix
- HExadecimal (base 16) - 0x

## Integer Suffixes
Integer literals can be suffixed to specify the size/type of the value:
- Unsigned - U
- Long - L
- Long Long - LL
Suffixes are generally only required when clarifying ambiguity of values where the user wishes to use a different type than the default type.
```c
#include <stdio.h>

printf("%d\d", 2147483648); // Treated as signed integer and throws warning
printf("%d\n", 2147483648U); // Treated as unsigned integer
```
### Floating Point Suffixes
As with integer types, floating point values can also be suffixed to specify which type to use.
- Float - f
- Double - d

### Character and String Literals
- Character - surrounded by single quotes 'A'
- String - surrounded by double quotes "Hello World"

## Flow Control
In assembly we used jumps and branching instructions to move around our code. C has flow control structures that are used for the same task.

### If Statements
C provides a standard branching control structure known as an if statement. This structure tests a condition and executes a block of code if that condition is true.
```c
if (condition)
{
	// Code to execute if condition is true
}
```
This structure can be nested and also supports else and else if statements.
```c
if (x > 1)
{
	// Code to execute if x is greater than 1
	if (x < 10)
	{
		// Code to execute if x is greater than 1 and less than 10
	}
}
else if (x < -1)
{
	// Code to execute if x is less than -1
	if (x > -10)
	{
		// Code to execute if x is less than -1 and greater than -10
	}
}
else 
{
	// Code to execute if x is not greater than 1 and not less than -1
}
```
### While Loops
The simplest loop structure in C is achieved by using a while loop. This loop executes a block of code while the condition is true.
```c
while (condition)
{
	// Code to execute while condition is true
}
```
A do while loop is similar to a while loop, but the loop will execute at least once.
```c
do 
{
	// Code to execute at least once
} while (condition);
```
This loop structure is typically accompanied by a looping variable known as an iterator:
```c
int i = 0; // iterator

// Execute code 10 times
while (i < 10)
{
	// Code to execute while i is less than 10
	i++
}
```
### For Loops
for loops are similar to while loops, but they usually result in more understandable code.
```c
for (initialisation; condition; increment)
{
	// Code to execute while condition is true
}
```
Note the initialisation and increment statements are optional, and while the conditon statement is also optional, we must ensure that the loop can terminate from within the structure (see next section)

### Break and Continue Statements
break and continue statements are used to terminate a loop early.
```c
for (int i = 0; i < 10; i++)
{
	if (i == 5)
	{
		break; // Terminate loop early
	}
	printf("%d\n", i);
}
```
```c
for (int i = 0; i < 10; i++)
{
	if (i == 5)
	{
		continue; // Skip current iteration and continue with next iteration
	}
	printf("%d\n", i);
}
```
If the loop is nested within another loop, the break and contiue statements will only terminate the innermost loop.
```c
for (int i = 0; i < 10; i++)
{
	for (int j = 0; i < 10; j++)
	{
		if (j == 5)
		{
			break; // Terminate inner loop early
		}
		printf("%d\n", j);
	}
}
```
## Expressions
C provides a number of operators which can be used to perform arithmetic/logical operations on values. C follows the same precedence rules as [[Mathematics]], however caution should be used when comparing precedence of certain logical and bitwise operations

### Arithmetic Operations
All arithmetic operations work as expected, noting that integer division is truncated. 

If an arithmetic operation causes a type overflow, the result will depend on the type. For signed integers, the result of an overflow is undefined in C. For unsigned integers, the result is truncated to the type size (or the value modulo the type size).

### Operator Types
- Unary operators - have a single operand. (++ and --, or + and -)
- Binary operators - have two operands (+,-, * and /)
- Ternary operators - have three operands (? :)

### Assignment Operator
To assign a value to a variable, use the assignment (=) operator
```c
int x = 5;
```
If we want to assign values to multiple variables of the same type, we can use the comma (,) operator
```c
int x = 1, y = 1, z = 3;
```
We can also use the assignment (=) operator to assign the same value to multiple variables of the same type.
```c
int x, y, z;
x = y = z = 5;
```
### Compound Assignment
Compound assignment operators perform the operation specified by the additional operator, then assign the result to the left operand
```c
char x = 0b110001010;
x |= 0b00000001; // x = 0b11001010 | 0b00000001 = 0b11001011

int y = 25;
y += 5; // y = 25 + 5 = 30

char z = 0b100000010
z <<= 1; // z = 0b10000010 << 1 = 0b00000100
```
### Bitwise Operations
Binary operators behave as expected in C
```c
char x = 0b110001010;
unsigned char y = 0b011000001;
```
Bitwise NOT (-):
```c
char a = -x // a = ~0b11001010 = 0b00110101
```
Bitwise AND (&):
```c
char b = x & y; // b = 0b11001010 & 0b01100001 = 0b01000000
```
Bitwise OR (|):
```c
char c = x | y; // c = 0b11001010 | 0b01100001 = 0b11101011
```
Bitwise XOR (^):
```c
char d = x ^ y; // d = 0b11001010 ^ 0b01100001 = 0b10101011
```
Left Shift (<<):
```c
char e = x << 1; // e = 0b11001010 << 1 = 0b10010100
```
Right Shift (>>):
```c
char f = x >> 1; // f = 0b11001010 >> 1 = 0b11100101 11 
char g = y >> 1; // g = 0b01100001 >> 1 = 0b00110000
```
### Increment and Decrement
Increment and decrement operators are unary operators that can be used to increment or decrement a variable by 1.
```c
int x = 5;  
x++; // x = 6
```
The increment and decrement opeators can be used as either prefix or postfix operators
```c
int x = 5;
int y = x++; // y = 5, x = 6 
int z = ++x; // z = 7, x = 7
```
Prefix operators are evaluated before the statement is executedl, while postfix operators are evaluated after the statment is executed

## The Preprocessor
The preprocessor processes C code before it is passed onto the compiler. The preprocessor strips out comments, handles preprocessor directives and replaces macros. Preoprocessors begin with the # character and no non-white space characters can appear on the line before the preprocessor directive.

### Includes
The include directive is used to include the contents of another file into the current file. This directive has two forms. 
- include < filename> - include header files for the C standard library and other header files associated with the target platform.
- include "filename" - include programmer-defined header files that are typically in the same directory as the file containing the directive.
When this directive is used, it is equivalent to copying the contents of the file into the current file, at the location of the directive. The include file is also preprocessed and may contain other include directives.

## Header Files
Object files containing compiled code can be linked into a program to allow programmers to call existing functions. For C to have knowledge of the functions in this object file, the authors of those functions should store the function prototypes in a header file.
Header files end in the .h extension. They can be included into the source file using the # include directive and can significantly reduce compile times by reducing the amount of code that needs to be compiled.
In the following example, we will define an add function and include it into another C program.
```c
// add.c
int add(int x, int y)
{
	return x + y;
}
```
This file is compiled to add.o. To allow the add function to be called from the main program, we need to create a header file containing the function prototype of add
```c
// add.h
int add(int x, int y); // The variable names are not required in the prototype
```
We can then include this header file into the main program
```c
#include <stdio.h> // Include printf definition (and other definitions)
#include "add.h" // Include add function definition

int main()
{
	int x = 5;
	int y = 10;

	int z = add(x, y);
	printf("%d\n", z);
	
	return 0;
}
```
## Definitions
The #define directive is used to define preprocessor macros. Whenever these macros appear in the source file, they are replaced with the value specified by the macros. Macros are a simple text teplacement mechanism, and this must be defined carefully to avoid invalid code from being generated.
```c
#include <stdio.h>
#define PI 3.14159265358979

int main()
{
	printf("%f/n", 2 * PI);
	return 0;
}
```
Aside from constant values, macros can also be used to create small compile-time "functions", that expand to code:
```c
#include <stdio.h>
#define MAX(x, y) ((x) > (y) ? : (y))
#define SQUARE(x) ((x) * (x))

int main()
{
	int x = 5;
	int y = 10;

	int area = SQUARE(side); // transformed into ((side) * (side));

	int z = MAX(x, y);
	print("%d\n", z);
	
	return 0;
```
Note that the semi-colon is omitted at the end of the macro definition, as it would also be substituded into the program. Only a single preprocessor directive can appear on a line, and the directives must occupy a single line (note that a backslash \\ can be used to break long lines).

```c
display_raw(0b0011100, 0b1001001);
displau_on();
```

```c
// VPORTB.OUT |= PIN5_bm

// VPORTB.OUT |= PIN5_bm

// VPORT.OUT &= ~PIN5_bm turns led on
```
```c
// Pull up resistor 
PORTA.PIN5CTRL |= PORT_PULLUPEN_bm
PORTA.PIN6CTRL |= PORT_PULLUPEN_bm
PORTA.PIN7CTRL |= PORT_PULLUPEN_bm

int pressed = 0;
for (;;) {
	if (!(VPORTA.IN & PIN4_bm)){
	pressed++;
	display_hex(pressed);
	}
}
//

int pressed = 0;
uint8_t lastval = 0;
for (;;) {
	if (!(VPORTA.IN & PIN4_bm)){
		if (lastval & PIN4_bm){
			pressed++;
			display_hex(pressed);
		}
	}
}

// count the number of seconds
uint8_t count = 0;
for (;;) {
	display_hex(count);
	_delay_ms 1000;
	count++
}
```
--- 
# Pointers
When a variable is declared, the compiler automatically allocates a block of memory to store that variable. If we want to access this block of memory indirectly, we must use a pointer. In C, pointers are declared as "pointing to" an object of another type.
```c
uint8_t *ptr; // Pointer to a uint8_t variable
```
This code declares a variable `ptr` that points to a `uint8_t` variable. Internally, a pointer contains a memory address, which on the ATtiny1626 is 16-bit.

## Addressing
When the location we want to access is known in advanced, pointers can be declared with a specific address:
```c
volatile uint8_t *ptr = (voltatile uint8_t *)0x0421; // The address of PORTB DIRSET
```
A more common usage of pointers is to reference other variables.
```c
uint8_t x = 5;
uint8_t *ptr = &x; // Address of x
printf("Values: %d == %d\nAddresses: %p == %p\n", *ptr, x, ptr, &x);
// Values: 5 == 5
// Addresses 0x16b4e7550 == 0x16b4e7550
```
The amperstand (&) operator is used to return the address of the variable x. Here the pointer type of `ptr` must match the type of x.

## Dereferencing
Once we have a pointer, we can access the value at the address it points to using the unary dereference operator *
```c
uint8_t x = 5;
uint8_t *ptr = &x; // Address of x

// Read the value at the address pointed to by ptr
uint8_t y = *ptr; // y = Value at ptr = 5

// Write the value 10 to the address pointed to by ptr
*ptr = 10; // Value at prt := 10
// x = 10 but y = 5
```
This is known as indirection, as we are indirectly accessing a value through a pointer. This can be used to accomplish the same thing as the load and store instructions (ld and st).
```c
uint8_t a = 123;
uint8_t *b = &a; // b points to a
uint8_t c = *b; // c contains 123
*b = 0; // Now a contains 0 (c in unchanged)
```

# Strings
In C, strings are represented as arrays of characters, terminated by a character with the value 0. Strings are declared using double quotes ("") and are automatically terminated by a null character.
```c
char *str = "Hello World";
printf("%s\n", str); // Prints "Hello World"\n

// Because str is a pointer, it can be printed directly.
printf(str); // Prints "Hello World"
printf("\n"); // Print "\n"
```
In the example above, the compiler automatically allocates a block of memory to store the string, which in this case is 13 bytes: 11 bytes for "Hello World", 1 byte for the newline "\n" and 1 byte for the 0 terminator. The pointer str points to the first character in the string.
```c
char *str = "Hello World";
*str == 'H'; // True
```
When using the `printf` function, the null terminator is required to indicate the end of the string. We will see how to index into strings in the section on arrays.

Below are alternative ways of declaring and initialising a string. 
```c
char myString[] = "cab403Program"; // String literal LEGAL
char ch[] = {'c', 'a', 'b', '4', '0','3', 'P', 'r', 'o', 'g', 'r', 'a', 'm', '\0'}; //char array LEGAL
char *cptr = "cab403Program"; // char pointer LEGAL
```
## String Input/Output
### Input
We can use `scanf()` to take a string input. The syntax for using `scanf()` function to take a string input without spaces.
```c
scanf("%s", char *s);
```
Here, `s` is a pointer which points to the array of characters where the input taken as a string will be stored.

To include space in the string input, there are a few methods to use. One of which is the scanset expression, which is denoted by `%[]`. Using this with `scanf()` will only process the characters specified inside the square brackets.

The expression `%[^\n]%*c` inside `scanf()` will take the complete line including spaces as a string input, alternatively `%[^\n]s` will also work. For example:
```c
char sentence[20];              // array to store string taken as input 
scanf("%[^\n]s", sentence); // take user input
```
#### gets()
`gets()` takes a complete line as input and stores it in the string provided as parameter. The function keeps reading in input until it encounters a newline character `\n`, once a `\n` isn't included it stops reading.
```c
char sentence[20];
gets(sentence);
```
However, `gets()` doesn't care about the size of the character array passed to it and will lead to buffer overflow if more than 30 characters is inputted.

#### fgets()
An alternative is using the `fgets()` function. The function is similar to `gets()` but we can also specify a maximum size for the string which will be taken as a string input from the user.
```c
char sentence[20]; 
fgets(sentence, 20, stdin); 
```
While the `gets()` function converts the `\n` character to `\0` to make it a null-terminated string, the `fgets()` function does not. Instead, it adds a `\0` symbol after the `\n` character to achieve the same

## Qualifiers
Various qualifiers can be used to modify the type of a pointer. Typically these qualifiers apply to the memory pointed to by the pointer. If the variable which the pointer points to is constant, the dereference operator cannot be used to reassign the value of the variable.
```c
const uint8_t a = 100; // Constant
uint8_t *ptr = &a; // Points to the constant 'a'
*ptr = 200; // Error: Cannot modify 'a' because 'a' is a constant
```
If the pointer is declared as constant, the pointer imposes a read-only restriction on the memory it points to.
```c
uint8_t a = 100; // Variable
uint8_t b = 200; // Variable

const uint8_t *ptr = &a; // Points to 'a' but treats it as a constant
ptr = &b; // Valid: 'ptr' is not a constant
```
If the qualifier is placed after the asterisk, the pointer itself is constant, meaning it cannot be reassigned to another address.
```c
uint8_t a = 100; // Variable
uint8_t b = 200; // Variable

uint8_t const *ptr = &a; // Points to 'a' but cannot be reassigned
*ptr = 200; // Valid: 'ptr' points to 'a' which is not constant
ptr = &b; // Error: Cannot reassign 'ptr'
```
If we wish, we can apply the qualifiers to both the pointer and the variable which that pointer points to.
```c
uint8_t a = 100; // Variable
uint8_t b = 200; // Variable

const uint8_t *const ptr = &a; // Points to 'a' but cannot be reassigned nor modified 
ptr = &b; // Error: Cannot reassign 'ptr'
*ptr = 200; // Error: Cannot modify 'a' because 'ptr' is constant
```
### Pointers to Pointers
Pointers can also point to other pointers
```c
uint8_t a = 100; // Variable

uint8_t *ptr = &a; // Points to 'a'
uint8_t **ptr2 = &ptr; // Points to 'ptr'
```
This can be used to modify the address of a pointer indirectly
```c
uint8_t a = 100; // Variable
uint8_t b = 200; // Variable

uint8_t *ptr = &a; // Points to 'a'
uint8_t **ptr2 = &ptr; // Points to 'ptr'

*ptr2 = &b; // 'ptr' now points to 'b'
```
For high levels of indirection, we can use more asterisks, althought this is unncommon. Qualifiers can also be applied to pointers to pointers:
```c
uint8_t a = 100; // Variable
uint8_t *ptr = &a; // Points to 'a'
const uint8_t **ptr1 = &ptr; // Pointer to pointer to constant uint8_t
uint8_t * const *ptr2 = &ptr; // Pointer to constant pointer to uint8_t
uint8_t ** const ptr3 &ptr; // Constant pointer to pointer to uint8_t
```
If this confused you, https://cdecl.org/ may help.

### Pointer Arithmetic
Pointers can be changed with arithmetic operators such as + and -. Arithmetic on pointers affects the address of the pointer, so that the pointer points to another location. When performing arithmetic on pointers, the size of an increment is determined by the type of the variable that the pointer is pointing to.
```c
uint8_t a = 100; // Varaible
uint8_t *ptr = &a; // Points to 'a'
ptr++; // Increment by 1 byte (size of uint8_t)
// ptr now points to the next byte after 'a'
```
### Void Pointers
When a pointer needs to point to a memory address of an unknown type, it can be declared with the void keyword.
```c
void *ptr; 
```
Void pointers have no type, so they cannot be derefereneced. Pointers of other types can be assigned to void pointers, but not vice versa.
```c
uint8_t a = 100;
void *ptr = &a; // Pointer to uint8_t
uint8_t *ptr2 = ptr; // Error: Cannot assign void pointer to uint8_t pointer
```
### Size-of
The `sizeof` function can be used to determine the size of a variable in bytes.
```c
uint8_t a = 100;
uint16_t b = 200;
sizeof(a); // Returns 1
sizeof(b): // Returns 2
``` 
---

# Arrays
Array types are used to hold multiple values of the same type in a contiguous block of memory. Arrays can be declared in the following ways:
```c
uint8_t a[10]; // Arrays of 10 uint8_t
uint8_t b[10] = {0}; // Array of 10 uint8_t initialised to 0
uint8_t c[] = {1, 2, 3}; // Array of 3 uint8_t initalised to 1, 2, 3
uint8_t d[5] = {1, 2, 3}; // Array of 5 uint8_t initialised to 1, 2, 3, 0, 0
```
The brace ({}) syntax can only be used to initalise an array and if the length of the array which is being assigned is less than the length of the array being assigned to, the remaining values will be set to 0.

### Character Arrays
A character array is a special type of array which is used to store strings. Character arrays can be declared using the `char` keyword.
```c
char a[] = "Hello World\n";
// Equivalent to:
char b[12] = {'H', 'e', 'l', 'l', 'o', ' ', 4 'W', 'o', 'r', 'l', 'd', '\0'};
```
This method allocated 13 bytes of SRAM and initilaises those bytes with the string "Hello World". This means that the string can be modified later in the program. If we use the const keyword, the string will be stored in flash memory and cannot be modified.
```c
const char a[] "Hello World\n";
```
### Indexing
Array elements can be accessed with the array index operator ([ ]). In C, array indices start at 0.
```c
uint8_t a[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
a[0]; // Returns 0
a[1] = 10; // a is now {0, 10, 2, 3, 4, 5, 6, 7, 8, 9}
```
It is undefined behaviour to access an array element which is out of bounds. However it is possible to have a pointer to an element one past the end of an array as long as the pointer is not dereferenced.
```c
uint8_t a[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
uint8_t *ptr = &a[10];
```
To loop through an array, we can use a for loop.
```c
uint8_t a[10];
for (uint8_t i = 0; i < 10; i++) {
	a[i] = i;
}
```
### Pointers and Arrays
Arrays are implicitly coverted to pointers to the first element of the array.
```c
uint8_t a[10];
uint8_t *ptr = a; // Equivalent to `uint8_t *ptr = &a[0]`
*ptr = 100; // 'a' is now {100, 0, 0, 0, 0, 0, 0, 0, 0, 0}
```
This is especially useful when passing arrays to functions, as arrays cannot be passed to functions by value, but rather the pointer to that array can. This lets us index into an array in a function and the changes will be reflected in the original array.
```c
void func(uint8_t *arr) {
	arr[0] = 100;
}

uint8_t a[10];
func(a); // `a` is now {100, 0, 0, 0, 0, 0, 0, 0, 0, 0}
```
The syntax `arr[i]` is equivalent to `*(arr + i)`.  This is possible because arrays are stored contiguously in memory. Note that it is not possible to change an array's address:
```c
uint8_t a[10];
a++ // Error: Cannot cange the address of an array
```
### Array Length
The length of an array can be determined with the `sizeof` function
```c
uint16_t array[] = {1000, 2000, 3000};
uint8_t arraysize = sizeof(array); // arraysize is 6
```
```c
uint8_t a[10];
uint16_t b[5];
sizeof(a) / sizeof(a[0]); // Returns 10
sizeof(b) / sizeof(b[0]); // Returns 5
```
We divide by the size of the first element of the array because the type of the array may be larger than 1 byte.

### Copying Arrays
Arrays can be copied in two ways. The first way is to use a for loop.
```c
uint8_t a[10];
uint8_t b[10];
for (uint8_t i = 0; i < sizeof(a) / sizeof(a[0]); i++) {
	b[i] = a[i];
}
```
The second way is to use the memcpy function from the string.h library
```c
uint8_t a[10];
uint8_t b[10];
memcpy(b, a, sizeof(a) / sizeof(a[0]));
```
### Multidimensional Arrays
Multi-dimensional arrays (or multiple subscript arrays) are used to hold mult-dimensional data.
```c
uint8_t a[][3] = {
	{1, 2, 3},
	{4, 5, 6},
	{7, 8, 9}
};
```
To declare a multi-dimensional array, all dimensions but the first need to be specified. The rows of the array must be specified witin additional braces ({ }). Elements can be accessed by specifying the index of each dimension.
```c
a[0][0]; // Returns 1
a[1][2]; // Returns 6
```
These arrays are also stored contigously in memory, in row-major order, and hence pointer arithmetic is performed differently.
```c
uint8_t a[][3] = {
	{1, 2, 3},
	{4, 5, 6},
	{7, 8, 9}
};

uint8_t rows = 3;
uint8_t cols = 3;

for (uint8_t i = 0; i < rows; i++) {
	for (uint8_t j = 0; j < cols; j++) {
		// Double indexing
		printf("%d ", a[i][j]);

		// Single indexing
		printf("%d ", a[i * cols + j]);

		// Pointer arithmetic
		printf("%d ", *(*(a + i) + j));
		// Equivalent to: printf("%d ", *(a[i] + j));
		// Each row is a pointer to the first element of that row
	}
}
```

## Functions
Procedures are called functions in C. Functions can return values and take arguements. The main function is the entry point of the program.

Functions in C must be declared in the top-level of a C program, and thus cannot be declared inside other functions. Functions are declared with the following syntax:
```c
return_type function_name(param_type param_name, ...) {
	// Function body
}
```
### Parameters
The parameters of a function are local variables scoped to that function
```c
uint8_t add(uint8_t a, uint8_t b) { // `a` and `b` are parameters of `add`
	return a + b;
}

int main(void) { 
	uint8_t a = 10; 
	uint8_t b = 20;

	uint8_t c = add(a, b); // `a` and `b` are arguments to `add`
}
```
To pass an array to a function, we can pass a pointer to that array. To do so, we must specify the length of the array as well.
```c
void print_array(uint8_t *arr, uint8_t len) {
	for (uint8_t i = 0; i < len; i++) {
		printf("%d ", arr[i]);
	}
}

int main(void) {
	uint8_t a[10];

	for (uint8_t i = 0; sizeof(a) / sizeof(a[0]); i++ ){
		a[i] = i;
	}
	print_array(a, sizeof(a) / sizeof(a[0]));
}
```
When a function does not take any arugments, we can specify `void` as the parameter list
```c
void func(void) {
}
```
### Return Values
To return a value from a function, we use the `return` keyword. When a function does not return a value, we can specify void as the return type. Note that a void function does not need to use the return keyword.

### Function Prototypes
C uses single-pass compilation, meaning that functions need to be declared before they can be called. Function prototypes are used to declare a function without having to specify the entire body of the function.
```c
uint8_t add(uint8_t a, uint8_t b); // Function prototype

int main(void) {
	uint8_t a = 10;
	uint8_t b = 20;

	uint8_t c = add(a, b);
}
uint8_t add(uint8_t a, uint8_t b) { 
	return a + b;
}
```
The compiler uses the function prototype to generate the code required to call the function without having to know the entire body of the function. The linker will then resolve all function calls to the appropriate function definitions. Note that parameter names are not required in function prototypes.

## Passing by Reference
As seen previously, we can pass variables by value and arrays by reference through pointers. As functions only return one value, we can use pointers to pass multiple values back to the caller. These output values are also passed to the function parameter list.
```c
void swap(uint8_t *a, uint8_t *b) {
	uint8_t temp = *a;
	*a = *b;
	*b = temp;
}
int main(void) {
	uint8_t a = 10;
	uint8_t b = 20;

	swap(&a, &b);
}
```
### Call Stack
As functions can call other functions, or even call themselves, local variables inside functions are stored on the stack. The return address of where a function is called from is also stored on the stack so that the program counter can be set to that address when the function returns. Local variables inside functions do not increase the explicit SRAM usage reported by the compiler. Rather, this memory will be allocated on the stack when the function is called. Therefore, it is important to ensure that the stack does not overflow, through recursive functions or large local variables.

### Scope
Variables and other identifiers in C have scope. Scope affects the visibility and lifecycle of variables. Scope is hierarchical, meaning that variables declared in a parent scope are visible to all child scopes. Variables declared in a child scope can also hide variables declared in a parent scope declared with the same name.

### Global Scope
Variables declared outside of any function are declared in the global scope. Global variables are visible to all functions in a progra.
```c
uint8_t a = 10; // Global variable

int main(void) {
	uint8_t b = 20; // Local variable

	a++; // 'a' is visible to 'main'
	return 0;
}
```
Global variables are allocated a fixed location in SRAM and do not exit on the stack.

### Local Scope
Variables declared inside a function are declared in the local scope. Thier lifetime is limited to the function in which they are declared. By default, local variables go on the stack.

### Block Scope
The block scope is a subset of the local scope. Variables declared inside blocks such as if statements have their own scope. these variables are only visible inside the block. We can create a new scope by using curly braces.

### Static Variables
When applied to a local variable, the static keyword changes the lifetime of a variable to the lifetime of the program. This means that the varialbe will not be destroyed when the function returns, and will retain its value between function call.s Static variables are allocated in SRAM and not on the stack. When applied to a global variable, the static keyword changes the visibility of the variable to the file in which it is declared.

# Types
## Accessing registers
As seen in [[C Programming#Addressing]], we can use the voltatile keyword to directly reference memory locations by address. This is useful for accessing memory mapped IO.
```c
volatile uint8_t *portb_outclr = 0x0426;
*portb_outclr = 0b00100000;
```
The `volatile` keyword is important because the variable is outside the control of the program. The compiler will therefore not optimise access to the variable. The `avr/io.h` header file includes macros and type definitions for accessing various registers on the AVR microcontroller.
```c
include <avr/io.h>
```
```c
if (~VPORTA.IN & PIN5_bm) {
	// button is pressed
}
```
### Type Casting
Some type conversions are implicit, such as converting a uint8_t to a uint16_t. However, some implicit type conversions generate warnings usually because of a loss of information, or because conversion is not portable across platforms.
Therefore, to explicity convert a variable to a different type, we can use the unary type casting operator.
```c
volatile uint8_t *portb_outclr = (volatile uint8_t *)0x0426;
```
This does not make code more portable, but it tells the compiler that the programmer is aware of the conversion that it is intentional.

Below is an example of type casting:
```c
int sum = 17, count = 5;
double mean;

mean = (double) sum / count;
printf("Value of mean : %f\n", mean ); // Value of mean : 3.400000
```
### Types of Type Casting
##### Numeric Types
Numeric types (signed or unsigned) will expand or narrow the type, resulting in the value being truncated or zero extended.
```c
(uint8_t-3 // 253)
```
##### Floating Point Types
Conversion from floating point to integer will truncate the fractional part.
```c
(uint16_t)-3.45 // -3
```
##### Pointer Types
Conversion between pointers will change the pointer type but will not affect the data. Note that these conversions are not portable across platforms.
```c
uint16_t a = 12345;
uint8_t *b = (uint8_t *)&a; // Likely 57, but may vary on different platforms
```
Casting an integer to a pointer will make the pointer contain the address in that integer.
```c
uint8_t *ptr = (uint8_t *)0x1234;
```
Likewise, casting a pointer to an integer will make the integer contain the address in the pointer.
```c
uint8_t *ptr = (uint8_t *)0x1234;
uint16_t addr = (uint16_t)ptr; // addr = 0x1234;
```
These conversions are not portable, but can be necessary when accessing memory mapped IO.

```c
int *p1, *p2;
double *q;
void *v;

// Legal assignments 
p1 = 0; // Same as null
p1 = (int *) 1;
p1 = p2;
p2 = v;
p1 = (int *) q; // Casts q into an int pointer, stores in p1.

// Illegal assignments
p1 = q;
p2 = 1;
```
### Void pointers and Type Casting
```c
void *ptr;    // Void pointer
char a = 'A'; // Character 'A'
int b = 2;    // Integer 2
float c = 3;  // Float 3

ptr = &a;     // Address of a
printf("\nThe value of a = %c\n",*((char*)ptr)); // The value of a = A

ptr = &b;
printf("\nThe value of b = %d\n",*((int*)ptr)); // The value of b = 2

ptr = &c;
printf("\nThe value of c = %f\n",*((float*)ptr)); // The value of c = 3.000000
```
##### Modifying Qualifiers
Casting can also be used to add/remove qualifiers such as `const` and `voltatile`, however the following will not work on the ATtinty1626 because the const qualifer usually results in that variable being stored in SRAM or read-only memory locations.
```c
const uint8_t a = 10;
const uint8_t *b = &a;

*((uint8_t *)b) = 20; // May lead to undefined behaviour
```
##### Avoiding Truncation
Casting can also be used to avoid truncation errors when performing arithmetic
```c
uint16_t a = 25000;
uint16_t b = 10000;

uint32_t c = a * b; // c = 45696 (incorrect)
uint32_t d = (uint32_t)a * b; // d = 250000000
```
# Memory





# Objects 
## Structures
Structures are way to group related data together.
```c
struct Point {
	uint8_t x;
	uint8_t y;
};
struct Point p;
```
The members of a structure can be accessed using the dot operator.
```c
p.x = 30;
p.y = 40;
```
Struct members can also be initialised using braces as with arrays.
```c
struct Point p = {30, 40};
```
Unlike arrays, structures can be passed between functions and copied normally.
```c
void func(struct Point p){
	p.x = 50;
}

struct Point p = {30, 40};
func(p);

struct Point q = p; // q.x = 50, p.y = 40
```
Due to this, structs ca contain arrays which can be passed and copied by placing them in structs. Along with this, functions can also return structs.
```c
struct Point funct() {
	struct Point p = {30, 40};
	return p;
}

struct Point p = func(); // p.x = 30, p.y = 40
```
### Memory Layout
Struct members are stored in memory in the order they are declared. If the platform has alignment requirments, the compiler will insert padding to ensure that the next member is aligned correctly. 
This is done to ensure that the compiler can access the members of the struct efficiently.

example from iotn1626.h
```c
// Virtual Ports 
typedef struct VPORT_struct
{
	register8_t DIR; // Data direction
	register8_t OUT; // Output value
	register8_t IN; // Input value
	register8_t INFLAGS; // Interupt flags
} VPORT_t;

#define VPORTA (*(VPORT_t *)0x0000) // Virtual Ports
#define VPORTB (*(VPORT_t *)0x0004) // Virtual Ports
#define VPORTC (*(VPORT_t *)0x0008) // Virtual Ports
```
### Anonymous Structures
Structures can be declared without a name if they only used once.
```c
struct {
	uint8_t x;
	uint8_t y;
} p;
```
The type of this variable is **unnamed**.

### Structures Inside Structures
Structures can contain other structures
```c
struct Point {
	uint8_t x;
	uint8_t y;
};

struct Rectangle {
	struct Point p1;
	struct Point p2;
};

struct Rectangle r = {{10, 20}, {30, 40}};
```
Another example:
```c
struct player {
	struct coord loc;
	uint8_t hp, sp;
	char name[8];
};

struct player p = {{2, 6}, 100, 50, "Tim"};
printf("%d %d", p.loc.x, p.loc.y); // Prints 2 6
```
### Structures and Pointers
Structures and members of structs can be addresed normally with the address-of operator.
```c
struct coord a = {3, 4};
uint8_t *b = &a.x;
*b = 5;
printf("%d %d", a.x, a.y); // Prints 5 4
```
There is a special operator used for accessing members of struct through a point: ->
```c
struct coord *ptr = &a;
ptr->x = 5; // Same as (*ptr).x
```
The -> operator exists because . has higher precedence than *

Example in use:
```c
struct Point p = {30, 40};
struct Point *ptr = &p;

ptr->x = 50; // Equivalent to (*ptr).x = 50
```
### Typedef
Typedefs can be used to give a type an alias so that the variables type is determined by the typedef instead of the actual type. If we want to use a structure multiple times, we can use a typedef to give it a (new) name.
```c
typedef struct PointStruct {
	uint8_t x;
	uint8_t y;
} Point;

Point p = {30, 40}; // Point is an alias to struct PointStruct
```
Alternative
```c
typedef struct PointStruct Point; // Now we can type 'cord' instead of 'struct coord'
int main(void) {
	coord a = {3, 4};
}
```
### Unions
Unions are similar to structures, however the members of a union share the same overlapping memory location. While structs have capacity to store multiple values, unions only have the capacity to store its largest value.
```c
union Character {
	char Character;
	uint8_t integer;
};

union Character c = {'A'};

printf("%c\n", c.character); // Prints 'A'
printf("%u\n", c.integer); // Prints 65
```
This use allows us to access the same memory location interpretted as a different type without the need of casting pointers.
When used with structs, the order members in those structs is also maintained.
```c
struct a {
	uint8_t i;
	float f;
};
struct b {
	uint8_t i;
	char c[4];
};

union u {
	struct a a;
	struct b b;
};

union u u;

u.a.i = 10;
u.a.f = 3.14;
// u.a.i = 10; u.a.f = 3.14

u.b.c[0] = 'A';
u.b.c[1] = 'B';
u.b.c[2] = 'C';
u.b.c[3] = 'D';

// u.b.i = 10; u.b.c = {'A', 'B', 'C', 'D'}

```

### Bitfields
Bitfields can be used within structures or unions to specify types of specific bit sizes.
```c
struct {
	uint8_t x : 4; 
	uint8_t y : 4; // x and y members are 4 bits each
} bits;

bits.x = 14;
bits.y = 7;

printf("%u\n", bits.x); // Prints 13
printf("%u\n", bits.y); // Prints 7
printf("%lu\n", sizeof(bits)); // Prints 1 (8 bits)
```
The base type of each member must be able to store the specified number of bits.

#### Properties of Bitfields
The address of a bitfield cannot be taken.
```c
struct {
	uint8_t x : 4;
	uint8_t y : 4;
}bits

uint8_t *ptr = &bits.x // Error
```
A bitfield cannot be an array.
```c
struct {
	uint8_t x : 4;
	uint8_t y[4] : 4;
}bits // Error
```
The name of a bitfield can be omitted, this will introduce padding.
```c
struct {
	uint8_t x : 4;
	uint8_t  : 4;
}bits
```
A zero-width bitfield can be used to align the next member to the next word boundary.
```c
struct {
	uint8_t x : 4;
	uint8_t  : 0;
	uint8_t y;
}bits

printf("%lu\n", sizeof(bits)); // Prints 2
```
# Compilation
C source code is translated into machine code through a compiler, whereas assembly code is translated into machine code through an assembler. While some compilers emit assembly code, others emit machine code directly.

## Assembler
Program code run directly on CPUs is not designed to be written by humans. The assembler prioritises performance ans size efficiency, and accounts for simplified chip design. They allow us to write programs in plain text without needing to memorise opcodes, or manaually keep track of memory locations. Modern assemblers also provide features such as macros that assist in writing code. While the scope of an assembler is limited, the programmer decides exactly which instructions are used and the assembler simply translates them into machine code.

## Compiler
A compiler is a program that translates source code written in a high-level language such as C. In a high level programming language, the desired program is described algorithmically by the programmer and the compiler produces an equivalent program which results in the same side effects when executed 

### Compilation Process
Compilers can be configured to product code in various ways. Compiling without optimisation will produce code which closely resembles the source code, so that it is easier to debug. This also means that code generation is faster. Compilers can also be configured to optimise code for minimum code size or maximum speed (or a combination of both)

### Advantages of Compilers
High level languages are more portable than assembly code, as they are not tied to a specific instruction set architecture. This means that the same source code can be used on another platform, granted that a compiler for that platform is avaliable. Compilers also allow us to write efficient code through the use of compiler optimisations, which can be difficult to achieve manually in assembly code.

### Disadvantages of Compilers
Some disadvantages of compilers are that hardware-specific features may only be avaliable from assembly requiring the use of inline assembly or assembly language macros. Precise timing of code is also difficult due to the inability to predict how the compiler generates code.

## Object Files
An object file is the output from the compilation or assembler phase. Object files mostly contain machine code, and also contain information about the symbols defined in the source code. Large modularised programs which split source code into multiple files can be compiled into object files with external references unresolved. This allows the linker to resolve the references and product a single executable file.

## Linker
The linker is a program that combines multiple object files and links them together to produce a single executable file. The linker resolves all external references and addresses are updated as required. The linking step is extremely fast compared to the compulation step, as only addresses need to be updated. The linker also performs some optimisations such as dead code elimination, which removes unused code.
In assembly, the `.global` directive can be used to make labels available to the linker.

##### Linker in Assembly
```c
// function.S
.global function

function:
	ret
// main.S
rcall function
```
In this example, both files can be compiled into object files even though the `function` label is not defined in `main.S`. The linker will resolve the reference to `function` and produce a sinlge executable file.

##### Linker in C
In C, top-level symbols are public by default, but can be made private to the current translation unit by using the `static` keyword.
```c
// main.C
static int a = 0;

// file1.c
a = 1; // Error: a is not visible
```
To make a symbol visible to other translation units, the `extern` keyword can be used.
```c
// main.C
external int a;
printf("%d\n", a); // Prints 5

// file1.c
int a = 5;
```
Any non-static symbols are implicitly global, and can be accessed from any translation unit.

# Floating Point Types
In C, floating point types are represented as 32-bit IEEE 754 single precision floating point numbers. The `float` type is a 32-bit floating point number and the `double` type is a 64-bit floating point number. 

A single precision floating point number has a 1-bit sign, 8-bit exponent, and 23-bit mantissa. As such, the range of a single precision floating point number is $-2^{127}...2^{127}$. A floating point number $f$ can be represneted as:
$$ f = (-1)^s(1+2^{-23}m)2^{e-127}$$
where s is the sign bit, m is the mantissa and e is the exponent. Note that values are not equally spaced. There are several special values that can be represented by floating point numbers.
- $e = 255 \rightarrow 2^{128}$:
	$-m=0$ (all 0s): INFINITY if $s=0$, -INFINITY if $s=1$
	$-m$ is not all 0s: NAN
- $e=0\rightarrow 2^{-126}$ (denormalised):
	$-m=0$ (all 0s): 0.0 if $s=0$, -0.0 if $s=1$
	$-m$ is not all 0s: Subnormal numbers

The flexibility of floating point numbers means that arithmetic operations are expensive if not performed on a Floating Point Unit (FPU). As AVR does not have an FPU, floating point operations must be handled using the ALU instructions which can be significantly slower tha integer operations. In addition, floating point operations require the `avr-libc` floating point library to be linked which increases the size of the program.



