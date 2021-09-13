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



*   **[C-12.36]** Consider the voting problem from Exercise C-12.35, but now suppose that we know the number $k < n$ of candidates running, even though the integer IDs for those candidates can be arbitrarily large. Describe an $O(n\log k)$-time algorithm for determining who wins the election.

**Hint:** Think of a data structure that can be used for sorting in a way that only stores `k` elements when there are only `k` keys.

## Implementation

* **[P-12.59]** Implement a nonrecursive, in-place version of the quick-sort algorithm, as described at the end of Section 12.2.2.



* **[P-12.61]** Perform a series of benchmarking tests on a version of merge-sort and quick-sort to determine which one is faster. Your tests should include sequences that are “random” as well as “almost” sorted.



*   **Task 2 assignment**.
