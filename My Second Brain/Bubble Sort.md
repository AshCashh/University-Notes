---
tags:
  - algorithm
Created: 2024-03-21T15:02:39+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Bubble sort, sometimes referred to as a sinking sort is a simple [[Sorting Algorithms|Sorting Algorithm]] that repeatedly steps through the input list element by element, comparing the current element with the one after it, swapping their values if needed. These passes through the list are repeated until no swaps have to be performed during a pass, meaning that the list has been fully sorted. The algorithm, which is a comparison sort is named for the way the larger elements "bubble" up to the top of the list.

This simple algorithm performs poorly in real world use and is primarily as an educational tool. More efficient algorithms such as quicksort, timsort or merge sort are used by the sorting libraries built into popular programming languages such a Python or Java.

## Example
```pseudo
	\begin{algorithm}
	\caption{BubbleSort(A[0..n-1])}
	
	
	\begin{algorithmic}
	\Comment{Sorts a given array by bubble sort}
	\Input{An array $A[0..n-1]$ of orderable elements}
	\Output{Array $A[0..n-1]$ sorted in nondecreasing order}
	\For{$i\gets 0 $ \To $n-2$}
	\For{$j\gets 0$ \To $n-2-i$}
	\If{$A[j+1]<A[j]$ Swap $A[j]$ and $A[j+1]$}
	\EndIf 
	\EndFor 
	\EndFor

	\end{algorithmic}
	\end{algorithm}
```

## Efficiency
By analysing the algorithms efficiency, with respect to the length $n$ of the array and the number of comparisons $A[j+1]>A[j]$ performed, we found: 
$$
C_{worst}(n)=\sum_{i=0}^{n-2}\sum_{j=0}^{n-2-i}1=\cfrac{n(n-1)}{2}\in \mathcal{O}(n^2)
$$
