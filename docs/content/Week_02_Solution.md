---
layout: page
title: Workshop 2 Solution
---



# Workshop: Basic DS & Algorithm Analysis

-----
## Discussion

* **[R-3.6]** Give an algorithm for finding the second-to-last node in a singly linked list in which the last node is indicated by a `null` next reference.

**Hint:** It is okay to have an algorithm running in linear time.
**Solution:**

```pseudocode
private Node<E> getSecondLast( ) {
    if (size < 2)
        throw new IllegalStateException("list must have 2 or more entries");

    Node<E> walk = head;
    while (walk ->next ->next != null)
    	walk = walk ->next;
    
    return walk;
}
```



* **[R-3.8]** Describe a method for finding the middle node of a doubly linked list with header and trailer sentinels by "link hopping", and without relying on explicit knowledge of the size of the list. In the case of an even number of nodes, report the node slightly left of center as the "middle". What is the running time of this method?

**Hint:** Consider a combined search from both ends. Also, recall that a link hop is an assignment of the form `p = p.getNext( );` or `p = p.getPrev( );`.
**Solution:** The following method runs in $O(n)$​ time.

```pseudocode
private Node<E> middle( ) {
    if (size == 0)
	    throw new IllegalStateException("list must be nonempty");
    Node<E> middle = header -> next
    Node<E> partner = trailer -> prev;
    while (middle != partner && middlee ->next != partner) {
        middle = middle.getNext( );
        partner = partner.getPrev( );
    }
    return middle;
}
```



*   **[C-3.23]** Suppose you are designing a multiplayer game that has $n ≥ 1000$​​​​​ players, numbered `1` to `n`, interacting in an enchanted forest. The winner of this game is the first player who can meet all the other players at least once (ties are allowed). Assuming that there is a method `meet(i, j)`, which is called each time a player `i` meets a player `j` (with $i \neq j$), describe a way to keep track of the pairs of meeting players and who is the winner.

**Hint:** You might want to consider using a two-dimensional array.
**Solution:** Define an $(n + 1) × (n + 1)$​​​​​​​​​​​​​​​​ two-dimensional boolean array `M`, which will record the meeting pairs. So that `M[i, j] = true` if and only if player `i` and `j` have met. In addition, define a one-dimensional integer array `c` of size $n+ 1$​​​​​​​​​​​ so that `c[i]` is a count of the number of other players that player `i` has met. When a player `i` and `j` meet, we check `M[i, j]`, and if it is true, then we are done—the players have already met. Otherwise, we set `M[i, j]` and `M[ j,i]` to true and we increment `c[i]` and
`c[j]`. If either `c[i]` or `c[j]` equals $n-1$ after this, then we have a winner.



*   **[C-3.25]** Describe an algorithm for concatenating two singly linked lists `L` and `M`, into a single list `L′` that contains all the nodes of `L` followed by all the nodes of `M`.

**Hint:** This concatenation operation need not search all of `L` and `M`.
**Solution:** Simply use a temporary node to walk to the end of list `L`. Then, make the last element of `L` point to the first element of `M` as its “next” node.



*   **[C-3.28]** Describe in detail an algorithm for reversing a singly linked list `L` using only a constant amount of additional space.

**Hint:** Consider changing the orientation of links while making a single pass through the list.
**Solution:** Such a method of the SinglyLinkedList class could be implemented as follows.

```java
public void reverse( ) {
	Node<E> prev = null;
	Node<E> walk = head;
    while (walk != null) {
        Node<E> adv = walk.getNext( );
        walk.setNext(prev);
        prev = walk;
        walk = adv;
    }
    head = prev;
}
```



* **[R-4.8]** Order the following functions by asymptotic growth rate.

1.   $4n\log n+2n$​​​
2.   $2^{10}$
3.   $2^{\log n}$​
4.   $3n+100\log n$​
5.   $4n$
6.   $2^n$
7.   $n^2 +10n$
8.   $n^3$
9.   $n\log n$​

**Hint:** Simplify the expressions, and then use the ordering of the seven important algorithm-analysis functions to order this set.
**Solution:** $2^{10}$ < $2^{\log n}$ == $3n+100\log n$ == $4n$ < $n\log n$ == $4n\log n+2n$ < $n^2 +10n$ < $n^3$ < $2^n$



**Code Fragment 4.12** for Question R-4.9 to R-4.13. 

```java
1 /∗∗ Returns the sum of the integers in given array. ∗/ 
2 public static int example1(int[ ] arr) { 
3 	int n = arr.length, total = 0;
4 	for (int j=0; j < n; j++) // loop from 0 to n-1
5 		total += arr[j];
6 	return total;
7 }
8
9 /∗∗ Returns the sum of the integers with even index in given array. ∗/
10 public static int example2(int[ ] arr) {
11 	int n = arr.length, total = 0;
12 	for (int j=0; j < n; j += 2) // note the increment of 2
13 		total += arr[j];
14 	return total;
15 }
16
17 /∗∗ Returns the sum of the prefix sums of given array. ∗/
18 public static int example3(int[ ] arr) {
19 	int n = arr.length, total = 0;
20 	for (int j=0; j < n; j++) // loop from 0 to n-1
21 		for (int k=0; k <= j; k++) // loop from 0 to j
22 			total += arr[j];
23 	return total;
24 }
25
26 /∗∗ Returns the sum of the prefix sums of given array. ∗/
27 public static int example4(int[ ] arr) {
28 	int n = arr.length, prefix = 0, total = 0;
29 	for (int j=0; j < n; j++) { // loop from 0 to n-1
30 		prefix += arr[j];
31 		total += prefix;
32 	}
33 	return total;
34 }
35
36 /∗∗ Returns the number of times second array stores sum of prefix sums from first. ∗/
37 public static int example5(int[ ] first, int[ ] second) { // assume equal-length arrays
38 	int n = first.length, count = 0;
39 	for (int i=0; i < n; i++) { // loop from 0 to n-1
40 		int total = 0;
41 		for (int j=0; j < n; j++) // loop from 0 to n-1
42 			for (int k=0; k <= j; k++) // loop from 0 to j
43 				total += first[k];
44 		if (second[i] == total) count++;
45 	}
46 	return count;
47 }
```



*   **[R-4.9]** Give a big-Oh characterization, in terms of `n`, of the running time of the example1 method shown in Code Fragment 4.12.

**Solution:** The `example1` method runs in $O(n)$​ time.

*   **[R-4.10]** Give a big-Oh characterization, in terms of `n`, of the running time of the example2 method shown in Code Fragment 4.12.

**Solution:** The `example2` method runs in $O(n)$ time.

*   **[R-4.11]** Give a big-Oh characterization, in terms of `n`, of the running time of the example3 method shown in Code Fragment 4.12.

**Solution:** The `example3` method runs in $O(n^2)$​ time.

*   **[R-4.12]** Give a big-Oh characterization, in terms of `n`, of the running time of the example4 method shown in Code Fragment 4.12.

**Solution:** The `example4` method runs in $O(n)$ time.

*   **[R-4.13]** Give a big-Oh characterization, in terms of `n`, of the running time of the example5 method shown in Code Fragment 4.12.

**Solution:** The `example3` method runs in $O(n^3)$​ time.

*   **[R-4.29]** Algorithm `A` executes an $O(logn)$-time computation for each entry of an array storing `n` elements. What is its worst-case running time?

**Hint:** The $O(\log n)$​ calculation is performed $n$ times.

*   **[R-4.30]** Given an $n$-element array `X`, Algorithm `B` chooses $\log n$ elements in `X` at random and executes an $O(n)$​-time calculation for each. What is the worst-case running time of Algorithm `B`?

**Hint:** The $O(n)$ calculation is performed $\log n$ times.

*   **[R-4.33]** Al and Bob are arguing about their algorithms. Al claims his $O(n\log n)$​-time method is always faster than Bob’s $O(n^2)$​-time method. To settle the issue, they perform a set of experiments. To Al’s dismay, they find that if $n < 100$, the
    $O(n^2)$-time algorithm runs faster, and only when $n \geq 100$ is the $O(n\log n)$-time one better. Explain how this is possible.

**Hint:** Discuss how the definition of the big-Oh fits into Al’s claim.
**Solution:** To say that Al’s algorithm is “big-Oh” of Bill’s algorithm implies that Al’s algorithm will run faster than Bill’s for all input
greater than some nonzero positive integer $n_0$. In this case, $n_0 = 100$.



## Implementation

* **[R-3.9]** Give an implementation of the `size( )` method for the `SingularlyLinkedList` class, assuming that we did not maintain size as an instance variable.

 **Hint:** Use a loop to traverse the list while counting.

 **Solution:**

```pseudocode
public int size( ) {
    int count=0;
    Node<E> walk = head;
    while (walk != null) {
        count++;
        walk = walk.getNext( );
    }
    return count;
}
```



* **[C-3.22]** Write a method, `shuffle(A)`, that rearranges the elements of array `A` so that every possible ordering is equally likely. You may rely on the `nextInt(n)` method of the `java.util.Random` class, which returns a random number between `0` and `n-1` inclusive.

**Hint:** Randomly choose the first element, then the second, and so on.



*   **[C-4.36]** Describe an efficient algorithm for finding the ten largest elements in an array of size `n`. What is the running time of your algorithm?

**Hint:** Note that 10 is a constant!
**Solution:** Since 10 is a constant, we can solve this problem for any size array in $O(n)$ time. We can begin by looping to find the largeste lement, and then record the index of that element in an auxiliary array of size 10. Then we find the next largest element with another loop, making sure to ignore the previously found element, and recording the index of the second largest element. Each such loop requires $O(n)$ time; the time to check if an index has already been used can be done in $O(1)$ time as
there are $O(1)$ entries in the auxiliary array. Therefore the overall time is $O(10*n)$​ which is $O(n)$.
