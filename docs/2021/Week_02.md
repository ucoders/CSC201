---
layout: page
title: Week 2 Content
---

# Learning outcomes
-----
1.   Understand and use Arrays, Linked Lists, and Double Linked Arrays
2.   Analyse algorithms with big-Oh notations



# Readings

-----
*   Chapter 3 & 4 of the textbook



# Workshop: Basic DS & Algorithm Analysis

-----
## Discussion

* **[R-3.6]** Give an algorithm for finding the second-to-last node in a singly linked list in which the last node is indicated by a `null` next reference.



* **[R-3.8]** Describe a method for finding the middle node of a doubly linked list with header and trailer sentinels by "link hopping", and without relying on explicit knowledge of the size of the list. In the case of an even number of nodes, report the node slightly left of center as the "middle". What is the running time of this method?



*   **[C-3.23]** Suppose you are designing a multiplayer game that has $n ≥ 1000$​​​​​ players, numbered `1` to `n`, interacting in an enchanted forest. The winner of this game is the first player who can meet all the other players at least once (ties are allowed). Assuming that there is a method `meet(i, j)`, which is called each time a player `i` meets a player `j` (with $i \neq j$), describe a way to keep track of the pairs of meeting players and who is the winner.



*   **[C-3.25]** Describe an algorithm for concatenating two singly linked lists `L` and `M`, into a single list `L′` that contains all the nodes of `L` followed by all the nodes of `M`.



*   **[C-3.28]** Describe in detail an algorithm for reversing a singly linked list `L` using only a constant amount of additional space.



* **[R-4.8]** Order the following functions by asymptotic growth rate.

1.   $4n\log n+2n$​​

2.   $2^{10}$
3.   $2^{\log n}$​
4.   $3n+100\log n$​
5.   $4n$
6.   $2^n$
7.   $n^2 +10n$
8.   $n^3$
9.   $n\log n$​



**Code Fragment 4.12**

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



*   **[R-4.10]** Give a big-Oh characterization, in terms of `n`, of the running time of the example2 method shown in Code Fragment 4.12.



*   **[R-4.11]** Give a big-Oh characterization, in terms of `n`, of the running time of the example3 method shown in Code Fragment 4.12.



*   **[R-4.12]** Give a big-Oh characterization, in terms of `n`, of the running time of the example4 method shown in Code Fragment 4.12.



*   **[R-4.13]** Give a big-Oh characterization, in terms of `n`, of the running time of the example5 method shown in Code Fragment 4.12.



*   **[R-4.29]** Algorithm `A` executes an $O(logn)$-time computation for each entry of an array storing `n` elements. What is its worst-case running time?



*   **[R-4.30]** Given an $n$-element array `X`, Algorithm `B` chooses $\log n$ elements in `X` at randoma nd executes an $O(n)$​-time calculation for each. What is the worst-case runningt ime of Algorithm `B`?



*   **[R-4.33]** Al and Bob are arguing about their algorithms. Al claims his $O(n\log n)$​-time method is always faster than Bob’s $O(n^2)$​-time method. To settle the issue, they perform a set of experiments. To Al’s dismay, they find that if $n < 100$, the
    $O(n^2)$-time algorithm runs faster, and only when $n \geq 100$ is the $O(n\log n)$-time one better. Explain how this is possible.



*   **[C-4.36]** Describe an efficient algorithm for finding the ten largest elements in an array of size `n`. What is the running time of your algorithm?



## Implementation

* **[R-3.9]** Give an implementation of the `size( )` method for the `SingularlyLinkedList` class, assuming that we did not maintain size as an instance variable.



* **[C-3.22]** Write a method, `shuffle(A)`, that rearranges the elements of array `A` so that every possible ordering is equally likely. You may rely on the `nextInt(n)` method of the `java.util.Random` class, which returns a random number between `0` and `n-1` inclusive.



