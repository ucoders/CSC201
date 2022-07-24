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



*   **[R-12.20]** Suppose `S` is a sequence of n values, each equal to 0 or 1. How long will it take to sort `S` with the merge-sort algorithm? What about quick-sort?



*   **[C-12.26]** Describe and analyze an efficient method for removing all duplicates from a collection `A` of n elements.



*   **[C-12.35]** Suppose we are given an n-element sequence `S` such that each element in `S` represents a different vote for president, where each vote is given as an integer representing a particular candidate, yet the integers may be arbitrarily large (even if the number of candidates is not). Design an $O(n\log n)$-time algorithm to see who wins the election `S` represents, assuming the candidate with the most votes wins.



*   **[C-12.49]** Bob has a set A of `n` nuts and a set B of `n` bolts, such that each nut in A has a unique matching bolt in B. Unfortunately, the nuts in A all look the same, and the bolts in B all look the same as well. The only kind of a comparison that Bob can make is to take a nut-bolt pair `(a,b)`, such that a is in A and `b` is in B, and test it to see if the threads of `a` are larger, smaller, or a perfect match with the threads of `b`. Describe and analyze an efficient algorithm for Bob to match up all of his nuts and bolts.

**Hint:** Try to design an efficient divide-and-conquer algorithm.



## Implementation

* **[P-12.59]** Implement a nonrecursive, in-place version of the quick-sort algorithm, as described at the end of Section 12.2.2.



* **[P-12.61]** Perform a series of benchmarking tests on a version of merge-sort and quick-sort to determine which one is faster. Your tests should include sequences that are “random” as well as “almost” sorted.



*   **Task 2 assignment**.
