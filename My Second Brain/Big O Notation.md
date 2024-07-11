---
tags:
  - algorithm
Created: 2024-03-08T14:25:14+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Big O notation is a [[Mathematics|Mathematical]] notation that describes the limiting behaviour of a [[Functions|Function]] when the argument tends towards a particular value or infinity.
![[Pasted image 20240415225322.png|center|300]]

In [[Computer System]], big O notation is used to classify [[Algorithm|Algorithms]] according to how their run time or space requirements grow as the input size grows. Big O classes ignore fine details such as multiplicative constants, bases of [[Exponents & Logarithms|Logarithms]] and low-order terms in polynomials. E.g. 
- An $O(n)$ algorithm will out perform $O(n^2)$ on average for large inputs
- An $O(2^n)$ algorithm will never work on large inputs 
## Efficiency Function to Big-O Notation
- $4n^2+2n-100\in O(n^2)$ 
- $400n^2 \in O(n^2)$ 
- $0.01n^2\in O(n^2)$
- $2n+100\in O(n)$

## Example: Element Uniqueness
Consider the following algorithm: 
```pseudo
\begin{algorithm}
    \caption{UniqueElements(A[0..n-1])}
    \begin{algorithmic}
	    \Comment{Determines whether all the elements in an given array are distinct\\}
	    \Comment{Input: An array A[0..n-1]\\}
	    \Comment{Output: Returns "true" if all the elements in A are distinct and "false" otherwise} 
	    \For{$i \gets 0$ \To $n-2$}
		    \For{$j\gets i+1$ \To $n-1$}
		    \If{ A[i]=A[j]}\Return{False}
		    \EndIf
		    \endfor
	    \EndFor
	    \Return{True}
      
      \end{algorithmic}
\end{algorithm}
```

The worst case is when all elements are unique or when only the last two elements are equal:
- The basic operation is done once in the innermost loop body
- The innermost loop occurs for $j$ equal to $i+1$ to $n-1$, inclusive:
$$\sum\limits^{n-1}_{j=i+1}1=(n-1)-(i+1)+1=n-i-1$$
- Outermost loop is performed for $i$ equal to $0$ to $n-2$, inclusive: 
$$\sum\limits^{n-2}_{i=0}(n-1-i)=(n-1)+(n-2)+\dots+1=\sum\limits^{n-1}_{i=1}i=\frac{n(n-1)}{2}$$
- Thus the algorithms worse-case efficiency is:
$$C_{worst}(n)=\frac{n(n-1)}{2}=\frac{1}{2}n^2-\frac{n}{2}\in O(n^2)$$
Probability Function:
$$f(n)=b \times \mathcal{n}c_1 + (1-b)\times \mathcal{n}^2c_1$$
