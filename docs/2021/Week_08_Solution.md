---
layout: page
title: CSC201 DSA
---

# Learning outcomes
1.   Explain and use Merge Sort
2.   Explain and use Quick Sort
3.   Explain and use Bucket-sort



# Readings

*   Chapter 12 of the textbook



# Workshop: Sorting and Selection



## Discussion

*   **[R-12.18]** Is the bucket-sort algorithm in-place? Why or why not?

**Solution:** No. Bucket-sort does not use a constant amount of additional storage. It uses $O(n+N)$ space.



*   **[R-12.20]** Suppose `S` is a sequence of n values, each equal to 0 or 1. How long will it take to sort `S` with the merge-sort algorithm? What about quick-sort?

**Solution:** Merge-sort takes $O(n\log n)$ time, as it is oblivious to the case when there are only two possible values. On the other hand, the way we have defined quick-sort with a three-way split implies that using quick-sort to sort `S` will take only $O(n)$ time.



*   **[C-12.26]** Describe and analyze an efficient method for removing all duplicates from a collection `A` of n elements.

**Solution:** First we sort the objects of `A`. Then we can walk through the sorted sequence and remove all duplicates. This takes $O(n\log n)$ time to sort and `n` time to remove the duplicates. Overall, therefore, this is an $O(n\log n)$-time method.



*   **[C-12.35]** Suppose we are given an n-element sequence `S` such that each element in `S` represents a different vote for president, where each vote is given as an integer representing a particular candidate, yet the integers may be arbitrarily large (even if the number of candidates is not). Design an $O(n\log n)$-time algorithm to see who wins the election `S` represents, assuming the candidate with the most votes wins.

**Solution:** Sort the votes, and then determine who received the maximum number of votes. First sort the sequence `S` by the candidate’s ID. Then walk through the sorted sequence, storing the current max count and the count of the current candidate ID as you go. When you move on to a new ID, check it against the current max and replace the max if necessary.



*   **[C-12.49]** Bob has a set A of `n` nuts and a set B of `n` bolts, such that each nut in A has a unique matching bolt in B. Unfortunately, the nuts in A all look the same, and the bolts in B all look the same as well. The only kind of a comparison that Bob can make is to take a nut-bolt pair `(a,b)`, such that a is in A and `b` is in B, and test it to see if the threads of `a` are larger, smaller, or a perfect match with the threads of `b`. Describe and analyze an efficient algorithm for Bob to match up all of his nuts and bolts.

**Hint:** Try to design an efficient divide-and-conquer algorithm.
**Solution:** This problem can be solved using a divide-and-conquer approach. First, we choose a random bolt and partition the remaining nuts around it. Then we take the nut that matches the chosen bolt and partition the remaining bolts around it. We can continue doing this until all the nuts and bolts are matched up. In essence, we are doing the randomized quicksort algorithm. Thus, we have an average running time of $O(nlog n)$.



## Implementation

* **[P-12.59]** Implement a nonrecursive, in-place version of the quick-sort algorithm, as described at the end of Section 12.2.2.



* **[P-12.61]** Perform a series of benchmarking tests on a version of merge-sort and quick-sort to determine which one is faster. Your tests should include sequences that are “random” as well as “almost” sorted.



*   **Task 2 assignment**.
