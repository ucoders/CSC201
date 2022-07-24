---
layout: page
title: CSC201 DSA
---

# Learning outcomes
1.   Understand the concept of recursion and can apply recursive calls to solve simple problems
2.   Understand and use Stack
3.   Understand and use Queue
4.   Explain the concept of deque



# Readings

*   Chapter 5 & 6 of the textbook



# Workshop: Recursion, Stacks, and Queues



## Discussion

*   **[R-5.1]** Describe a recursive algorithm for finding the maximum element in an array, A, of n elements. What is your running time and space usage?



*   **[R-5.10]** Describe a way to use recursion to compute the sum of all the elements in an $n \times n$ (two-dimensional) array of integers.



*   **[C-5.12]** Describe an efficient recursive algorithm for solving the element uniqueness problem, which runs in time that is at most $O(n^2)$ in the worst case without using sorting.



*   **[C-5.16]** In the Towers of Hanoi puzzle, we are given a platform with three pegs, `a`, `b`, and `c`, sticking out of it. On peg `a` is a stack of `n` disks, each larger than the next, so that the smallest is on the top and the largest is on the bottom. The puzzle is to move all the disks from peg `a` to peg `c`, moving one disk at a time, so that we never place a larger disk on top of a smaller one. See Figure 5.15 for an example of the case $n = 4$​​​. Describe a recursive algorithm for solving the Towers of Hanoi puzzle for arbitrary `n`. (Hint: Consider first the subproblem of moving all but the $n^{th}$​ disk from peg `a` to another peg using the third as “temporary storage.”)

<img src="src/Fig.5.15_Hanoi.jpg" alt="Figure 5.15" style="zoom:20%;" />



*   **[C-5.21]** Given an unsorted array, `A`, of integers and an integer `k`, describe a recursive algorithm for rearranging the elements in `A` so that all elements less than or equal to `k` come before any elements larger than `k`. What is the running time of your algorithm on an array of `n` values?



*   **[C-5.22]** Suppose you are given an array, `A`, containing `n` distinct integers that are listed in increasing order. Given a number `k`, describe a recursive algorithm to find two integers in `A` that sum to `k`, if such a pair exists. What is the running time of your algorithm?



*   **[R-6.1]** Suppose an initially empty stack `S` has performed a total of 25 push operations, 12 top operations, and 10 pop operations, 3 of which returned `null` to indicate an empty stack. What is the current size of `S`?



*   **[R-6.3]** What values are returned during the following series of stack operations, if executed upon an initially empty stack? push(5), push(3), pop(), push(2), push(8), pop(), pop(), push(9), push(1), pop(), push(7), push(6), pop(), pop(), push(4), pop(), pop().



*   **[R-6.7]** Suppose an initially empty queue `Q` has performed a total of 32 enqueue operations, 10 first operations, and 15 dequeue operations, 5 of which returned null to indicate an empty queue. What is the current size of Q?



*   **[R-6.9]** What values are returned during the following sequence of queue operations, if executed on an initially empty queue? enqueue(5), enqueue(3), dequeue(), enqueue(2), enqueue(8), dequeue(), dequeue(), enqueue(9), enqueue(1), dequeue(), enqueue(7), enqueue(6), dequeue(), dequeue(), enqueue(4), dequeue(), dequeue().



*   **[C-6.20]** Suppose you have three nonempty stacks `R`, `S`, and `T`. Describe a sequence of operations that results in `S` storing all elements originally in `T` below all of `S`’s original elements, with both sets of those elements in their original order. The final configuration for `R` should be the same as its original configuration. For example, if `R = (1,2,3), S = (4,5)`, and `T = (6,7,8,9)`, when ordered from bottom to top, then the final configuration should have `R = (1,2,3)` and `S = (6,7,8,9,4,5)`.



*   **[C-6.24]** Suppose you have a stack `S` containing `n` elements and a queue `Q` that is initially empty. Describe how you can use `Q` to scan `S` to see if it contains a certain element `x`, with the additional constraint that your algorithm must return the elements back to `S` in their original order. You may only use `S`, `Q`, and a constant number of other primitive variables.



## Implementation

* **[C-5.18]** Write a short recursive Java method that determines if a string `s` is a palindrome, that is, it is equal to its reverse. Examples of palindromes include 'racecar' and 'gohangasalamiimalasagnahog'.



*   **[P-5.30]** Write a program that can solve instances of the Tower of Hanoi problem (from Exercise C-5.16).



*   **[C-6.18]** In Code Fragment 6.8 we assume that opening tags in HTML have form `<name>`, as with `<li>`. More generally, HTML allows optional attributes to be expressed as part of an opening tag. The general form used for expressing an attribute is `<name attribute1="value1" attribute2="value2">`; for example, a table can be given a border and additional padding by using an opening tag of `<table border="3" cellpadding="5">`. Modify Code Fragment 6.8 so that it can properly match tags, even when an opening tag may include one or more such attributes.



*   **[P-6.36]** When a share of common stock of some company is sold, the capital gain (or, sometimes, loss) is the difference between the share’s selling price and the price originally paid to buy it. This rule is easy to understand for a single share, but if we sell multiple shares of stock bought over a long period of time, then we must identify the shares actually being sold. A standard accounting principle for identifying which shares of a stock were sold in such a case is to use a FIFO protocol—the shares sold are the ones that have been held the longest (indeed, this is the default method built into several personal finance software packages). For example, suppose we buy 100 shares at `$20` each on day 1, 20 shares at `$24` on day 2, 200 shares at `$36` on day 3, and then sell 150 shares on day 4 at `$30` each. Then applying the FIFO protocol means that of the 150 shares sold, 100 were bought on day 1, 20 were bought on day 2, and 30 were bought on day 3. The capital gain in this case would therefore be $100 \times 10 + 20 \times 6 + 30 \times (-6)$​​, or `$940`. Write a program that takes as input a sequence of transactions of the form “buy `x` share(s) at `$y` each” or “sell `x` share(s) at `$y` each,” assuming that the transactions occur on consecutive days and the values `x` and `y` are integers. Given this input sequence, the output should be the total capital gain (or loss) for the entire sequence, using the FIFO protocol to identify shares.

