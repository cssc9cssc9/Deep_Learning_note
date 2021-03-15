# Algorithm
- Algorithm is like programming recipe
- We can discuss algorithm with several part, like
	1. input(problem/data)
	2. output(correctness)
	3. definitenes(instruction)
	4. finitness(efficiency)
	5. effectiveness(computability)

### Correctness proof of algorithm
You should consider correctness of algorithm
write down the goal like
> `getMinIndex` returns $m$ such that $arr[m]$ is the smallest among $arr[0]$, $arr[1]$, $\dots$, $arr[len-1]$.

, and we write down the algorithm 

> ##*return the index to min element in $arr[0]\dots arr[len-1]$*
> **int** getMinIndex(**int** $arr[]$, **int** len){
> $\qquad$**int** $i$;
> $\qquad$**int** $m=0$;
> $\qquad$**for**($i=0; i<len; i$++){
> $\qquad\qquad$**if**($arr[m]>arr[i]$){
> $\qquad\qquad\qquad m=i$
> $\qquad\qquad$}
> $\qquad$**return** $m$
> }

then you should check every part of algorithm

> Lemma (loop invariance)
> After the $i$-th iteration of the *for* loop, $arr[m]$ is always the smallest among $arr[0]$, $arr[1]$, $\dots$, $arr[i]$.
> - true when $i=0$ ?
> - true when $i=k\rightarrow$ true when $i=k+1$ ?

### Efficiency of algorithm
There are a lot of way to improve the efficient, like
- Consider the probability of parallel computation make the algorithm more efficient.
- **Complexity** of algorithm can evaluate the load of memory which can help you determine efficiency of algorithm.

### Expression of pseudo code
Pseudo code is *spoken language* of programming
> getMinIndex($A$)
> 1  $m=1$
> 2  **for** $i=2$ **to** *A.length*
> 3 $\qquad$ // update if $i$-th element smaller
> 4 $\qquad$ **if** $A[m]>A[i]$
> 5 $\qquad\qquad m=i$
> 6 **return** $m$

>selection_sort($A$)
>1 **for** $i=1$ **to** $A$.*length*
>2 $\qquad$ s = getMinIndex($A[i,\dots,len]$)
>3 $\qquad$ SWAP($A[i]$,$A[s]$)
>4 **return** $A$, whcih has been sorted in place

For the case following, pseudo can avoid the person who does not understand about specific programming language and help person to comprehend.


