---
tags:
  - algorithm
Created: 2024-04-15T21:48:43+10:00
Modified: 2024-07-10T18:39:02+10:00
---
In [[Computer Science]], a binary tree is a [[Trees]] [[Linear Data Structures|Data Structure]] in which each node has a most two children, referred to as the 'left child' and the 'right child'. That is it is a k-ary tree with $k=2$. A [[Recursion|Recursive]] definition using [[Set Theory]] is that a binary tree is a [[Tuple]] (L, S, R) where L and R are binary trees or the empty set $\emptyset$ and S is a singleton set containing the root.
![[Pasted image 20240415215210.png|center|300]]
# Traversal 
Often we want to visit each of the nodes in a binary tree and examine the value there. There are three common orders in which the nodes can be visited:
1. Preorder Traversal (current-left-right): Visit the root first, then traverse the left sub tree in pre-order then traverse the right subtree in pre-order. 
1. In order Traversal (left-current-right): Traverse the left subtree in-order then visit the root, then traverse the right subtree in order
2. Post order Traversal (left-right-current): Traverse the left subtree in post order, then traverse the right then the root.
The efficiency for tree traversal algorithms are $\mathcal{O}(n)$. 

# Binary Search Tree
In a binary search tree (BST), for each node:
- All nodes in the left subtree have smaller values.
- All nodes in the right subtree have greater values.
Any operation must maintain the BST property.

 