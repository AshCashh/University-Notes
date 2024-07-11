---
tags: [algorithm]
Created: 2024-04-15T22:28:43+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Merge sort is an efficient general-purpose and comparison-based [[Sorting Algorithms|Sorting Algorithm]]. Most implementations produce a stable sort, meaning that the relative order of equal elements is the same in the input and output. Merge sort is a divide and conquer algorithm.

![[Merge-sort-example-300px.gif]]

Conceptually a merge sort works as follows:
1. Divide the unsorted list into $n$ sublists, each containing one element
2. Repeatedly merge sublists to produce a new sorted sublists until there is only one sublist remaining.

## Pseudocode
```pseudo
	\begin{algorithm}
	\caption{Merge(A[i...j], m)}
	\begin{algorithmic}
	\Comment{Merges sorted subarrays A[i...m] and A[m + 1...j] into a sinlge sorted subarray A[i...j], via temporary array T[i...j]}
	
	\While{$p\leq m$ \And $q\leq j$}
	\If{$A[p]\leq A[q]$}
	\State{$T[r]\gets A[p]$}
	\State{$p\gets p+1$}
	
	\Else\State{$T[r]\gets A[q]$}
	\State{$q\gets q+1$}
	\EndIf
	\State{$r\gets r+1$}
	\If{$p\leq m$}
	\State{$T[r...j]\gets A[p...m]$}
	\EndIf 
	\If{$q\leq j$}
	\State{$T[r...j]\gets A[q...j]$}
	\EndIf 
	\State{$A[i...j]\gets T[i...j]$}
    \EndWhile

	\end{algorithmic}
	\end{algorithm}
```

# Efficiency of Merge Sort
Time efficiency:
- In the worst case: $C_{worst}(n)\in\mathcal{O}(n\log(n))$, where $n$ is the length of the array
- In the average case: $C_{average}(n)\in\mathcal{O}(n\log(n))$
