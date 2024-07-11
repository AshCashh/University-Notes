---
tags:
  - algorithm
Created: 2024-03-21T13:52:23+10:00
Modified:
  - 2024-07-10T18:43:19+10:00
append_modified_update: true
---
The binary search algorithm is a type of [[Search Algorithms|Searching Algorithm]].
If we know that the collection of items is sorted according to some recognised ordering criterion, we can use a **decrease-and-conquer** algorithm to improve searching efficiency. A decrease-and-conquer algorithm decreases a problem instance to a smaller instance of the same problem and then conquers the problem by solving the smaller instance of the problem.
How does a binary search algorithm work?
1. Choose the midpoint of the array
2. If the item of interest there the search is finished
3. If the search key is smaller than the value at the midpoint, repeat the search on the lower half of the array
4. If the search key is larger than that value, repeat the search on the upper half of the array
```pseudo
\begin{algorithm}
\caption{BinarySearch(A[0..n-1], K)}
\begin{algorithmic}
	\Comment{Implement nonrecursive binary search\\}
	\Comment{Input: An array A[0..n-1] sorted in ascending order and a search key K\\}
	\Comment{Output: An index of the array's element that is equal to K or -1 if no element}
	\State $l\gets;r\gets n-1$
	\While{$l\leq$}
		\State $m\gets\lfloor (l+r)/2\rfloor$
		\If{$K=A[m]$}
			\Return m
		\Elif{$K<A[m]$}
		\State $r\gets m-1$
		\Else 
		\State $l\gets m+1$
		\EndIf
		
		
		
	\EndWhile
	\Return -1
	
\end{algorithmic}
\end{algorithm}
```
### Efficiency 
The worst case scenario for the binary search algorithm occurs when $K$ is not present in the sorted array. The basic operation is the comparison between $K$ and $A[m]$, including $K=A[m]$ and $K>A[m]$.

By analysing the algorithms efficiency, with respect to the length $n$ of the array and the number of comparisons between $A[m]$ and $K$ performed including $K=A[m]$ and $K>A[m]$. We find:
$$C_{worst}(n)=\log_2n+1\in O(\log n)$$
