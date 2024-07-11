---
tags: [algorithm]
Created: 2024-03-21T13:50:47+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A sequential [[Search Algorithms|Search Algorithm]] is a brute-force algorithm, an exhaustive problem-solving approach that systematically considers every possible solution and checks whether it satisfies the problem's conditions. Sequential search also know as linear search is performed by checking each element of the collection one by one until the desired element is found or the entire array has been examined.

```pseudo
\begin{algorithm}
    \caption{SequentialSearch(A[0..n-1], K)}
    \begin{algorithmic}
	    \Comment{Searches for a given value in a given array by sequential search\\}
	    \Comment{Input: An array A[0..n-1] and search key K\\}
	    \Comment{Output: The index of the first element of A that matches K or -1 if no match} 
	    \State $i \gets 0$
		\While{$i<n$ \And $A[i] \neq K$}
			\State $i \gets i + 1$
			    \EndWhile
		\If{$i<n$}\Return i
        
        \Else\Return $-1$
        \EndIf
      \end{algorithmic}
\end{algorithm}
```
### Efficiency
We choose comparison $A[i]\neq K$ as the basic operation in this case and assume that this comparison is not performed if the first conjunct $i<n$ is false. The worst case is when the key $K$ does not appear in array $A$ at all, or is the last item in the array, which forces the algorithm to inspect all $n$ items:
$$C_{worst}(n)=n\in O(n)$$

