---
layout: page
title: CSC201 DSA
---

# Learning outcomes
1.   Explain Boyer-Moore Algorithm as a solution of pattern pre-processing
2.   Explain the techniques of text pre-processing, including tries, compressed tries, and suffix tries
3.   Understand the concept of Greedy Method and explain the construction of Huffman’s Algorithm



# Readings

*   Chapter 13.1-13.2.2, 13.3, and 13.4 of the textbook



# Workshop: Text Processing

## Discussion

*   **[R-13.4*]** Draw a figure illustrating the pattern matching for the text `"aaabaadaabaaa"` and pattern `"aabaaa"` done by the Boyer-Moore algorithm.



*   **[R-13.8]** Draw a standard trie for the following set of strings: 
    { abab, baba, ccccc, bbaaaa, caa, bbaacc, cbcc, cbca }.

**Hint:** Use the online animation: <https://cmps-people.ok.ubc.ca/ylucet/DS/Trie.html>



*   **[R-13.9]** Draw a compressed trie for the strings given in the previous problem.

**Hint:** Use the online animation: <https://cmps-people.ok.ubc.ca/ylucet/DS/CompressedTrie.html>



*   **[R-13.11]** Draw the frequency array and Huffman tree for the following string: `"dogs do not spot hot pots or cats"`.

**Hint:** Don’t forget to include the space character. Use the online animation: <https://cmps-people.ok.ubc.ca/ylucet/DS/Huffman.html>



*   **[C-13.39]** In the art gallery guarding problem we are given a line `L` that represents a long hallway in an art gallery. We are also given a set $X = {x_0,x_1, . . . ,x_{n−1}}$ of real numbers that specify the positions of paintings in this hallway. Suppose that a single guard can protect all the paintings within distance at most 1 of his or her position (on both sides). Design an algorithm for finding a placement of guards that uses the minimum number of guards to guard all the paintings with positions in $X$.

**Hint:** Use a greedy algorithm.



## Implementation

* **Task 2 assignment**.

