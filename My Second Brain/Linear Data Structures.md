---
tags: [cs]
Created: 2024-03-14T13:41:17+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Linear Data Structures are a type of data structure in [[Computer Science]] where data elements are arranged sequentially or linearly. Each element has a previous and adjacent, except for the head and tail (first and last elements). 

## Characteristics 
- **Sequential Organisation**: In LDS, data elements are arranged sequentially, one after the other. Each element has a unique predecessor (except for the head) and a unique successor (except for the tail)
- **Order Preservation**: The order in which elements are added to the data structure is preserved. This means that the first element added will be the first one to be accessed or removed and visa versa. 
- **Fixed or Dynamic Size**: LDS can have either fixed or dynamic sizes. Arrays typically have a fixed size when they are created, while other structure like linked lists, stacks and queues can dynamically grow or shrink.
- **Efficient Access**: Accessing elements within a LDS is typically efficient. For example, arrays offer constant-time access to elements using their index.

LDS are commonly used for organising and manipulating data in a sequential fashion. Some of the most common LDS include:
- Arrays: A collection of elements stored in contiguous memory locations
- Linked Lists: A collection of nodes, each containing an element and a reference to the next node.
- Stacks: A collection of elements within Last-In-First-Out (LIFO) order
- Queues: A collection of elements with First-In-First-Out (FIFO) order

## Array
An array is a collection of items of same data type stored at contiguous memory locations.
Characteristics of Array Data Structure:
- **Homogeneous Elements:** All elements within an array must be of the same data type.
- **Contiguous Memory Allocation:** In most programming languages, elements in an array are stored in contiguous (adjacent) memory locations.
- **Zero-Based Indexing:** In many programming languages, arrays use zero-based indexing, which means that the first element is accessed with an index of 0, the second with an index of 1, and so on.
- **Random Access:** Arrays provide constant-time (O(1)) access to elements. This means that regardless of the size of the array, it takes the same amount of time to access any element based on its index.
### Types of arrays:
- **One-Dimensional Array:** This is the simplest form of an array, which consists of a single row of elements, all of the same data type. Elements in a 1D array are accessed using a single index.
- **Two-Dimensional Array:** A two-dimension array often referred to as a matrix or 2D array is an array of arrays
- **Multi-Dimensional Array:** Arrays can have more than two dimensions, leading to multi-dimensional arrays. These are used when data needs to be organised in a multi-dimensional grid.

## Linked List
A Linked List is a linear data structure which looks like a chain of nodes, where each node contains a data field and a reference (link) to the next node in the list. Unlike arrays, linked list elements are not stored at a continuous location

### Types of Linked Lists:
- Singly Linked List: In this type of linked list, every node stores the address or reference of the next node in the list and the last node has the next address or reference as NULL. For example: 1->2->3->4->NULL
- Doubly Linked List: In a doubly linked list, each node has two pointers: one pointing to the next node and one pointing to the previous node. This bidirectional structure allows for efficient traversal in both directions.
- Circular Linked Lists: A circular linked list is a type of linked list in which the first and the last nodes are also connected to each other to form a circle, there is no NULL at the end.

## Linked List vs Array
Both arrays an linked lists can be used to implement a more abstract data structure called list, which is a sequence of items. The basic operations performed on lists are accessing, searching for, inserting and deleting an item. 
- To access the $k^{th}$ entry in an array or linked list:
	- In an array its accessed using an index `item[k]`
	- In a linked list, we must step through the first `k-1` nodes
- To insert an item to the beginning of an array or linked list:
	- In an array we must move all the elements in the array before we can insert an item, which is inefficient
	- In a linked list, we can directly insert the item to the beginning
- To delete an item from an array or linked list:
	- In an array we must move all the items after the deletion
	- In a linked list, we do not need to move but need to traverse the pointer chain to find the pointer to the predecessor and the pointer to the successor of the node containing the item to be deleted.
- To search an item in array or linked list:
	- In an array we can search the array sequentially or use binary search if the items in the array are sorted
	- In a linked list, we need to traverse the pointer chain to find the node

