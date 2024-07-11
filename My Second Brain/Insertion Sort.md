---
tags: [algorithm]
Created: 2024-03-21T13:48:43+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Insertion sort is a simple [[Sorting Algorithms|Sorting Algorithm]] that builds the final sorted array (or list) one item at a time by comparison. It is much less efficient on large lists than more advanced algorithms.
![[Insertion_sort.gif|center]] 

The basic idea behind the insertion sort is:
1. Divide a list into two sections: a sorted section and a unsorted section
2. From the first element to the last element in the unsorted section:
	- Remove it from the unsorted section;
	- Insert it into the sorted section at a position such that after the insertion the sorted section remains sorted.
## Example
Below is a pseudocode example of a basic insertion sort:
```pseudo
	\begin{algorithm}
	\caption{InsertionSort(A[0..n-1])}
	\begin{algorithmic}
	\Comment{Sorts a given array by insertion sort}
	\Input{An array A[0..n-1] of $n$ orderable elements}
	\Output{Array A[0..n-1] sorted in nondecreasing order}
	\For{$i\gets 1$ \To $n-1$}
	\State{$v\gets A[i]$}
	\State{$j\gets i-1$}
	\While{$j\geq 0 $ \And $A[j]>v$}
	\State{$A[j+1]\gets A[j]$}
	\State{$j\gets j-1$}
	\EndWhile
	\State{$A[j+1]\gets v$}
    \EndFor

	\end{algorithmic}
	\end{algorithm}
```

# Efficiency 
By analysing the algorithm's efficiency, with respect to the length $n$ of the array and the number of comparisons $A[j]>v$ performed we find:
$$C_{worst}(n)=\sum\limits^{n-1}_{i=1}\sum\limits^{i-1}_{j=1}1=\sum\limits^{n-1}_{i=1}i=\cfrac{n(n-1)}{2}\in\mathcal{O}(n^2)$$

