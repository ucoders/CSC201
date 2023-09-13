---
layout: page
title: CSC201 DSA Task 2
---

# Background

Since Bitcoin users are anonymous, there is a need to maintain a record of users reputation to prevent transactions with fraudulent and risky users. People who trade using Bitcoin on a platform called Bitcoin OTC (http://www.bitcoin-otc.com/) rate other members in a scale of -10 (total distrust) to +10 (total trust) in steps of 1, resulting in a who-trusts-whom network. This is the first explicit weighted signed directed network available for research.

The dataset for the assignment was Bitcoin OTC trust rating. One record/row represents a directed edge A->B which means user A rated on B with a score. For example, in the following record, user #6 rated user #2 with 4.

| SOURCE | TARGET | Rating |
| ------ | ------ | ------ |
| 6      | 2      | 4      |



The data is available in the starter code once your initiate the project in the Gitub classroom. The original data source is from <https://snap.stanford.edu/data/soc-sign-bitcoin-otc.html>

The objective of this project is to develop a query system for these trust ratings. There are two key components are required. 

### Component 1: Average Rating and Ranking Query

The primary goal of this component focuses on calculating and sorting `average_rating` for each member, allowing queries for ranking orders.

`average_rating` is an important measurement for the trustworthy of a member. The `average_rating` for a given member `i` is defined as:
$$
\text{Average Rating of i} = {\text{Sum of Ratings Received by i} \over \text{Total Number of Ratings Received by i}}
$$

#### Requirements

1. **Average Rating**: Implement an algorithm to compute the average rating for each user.
2. **Sorting Algorithms**: Implement ***three different sorting algorithms*** to sort the dataset based on the calculated `average_rating`. Name each code file based on its sorting algorithm, such as `MergeSort.java`.
3. **Get Method**: Each sorting algorithm implementation should include a method `get(int rank)` that prints all member IDs with the given ranking order, and their average rating value. The ranking is based on `average_rating`.
   - `get(1)` should return the user(s) with the highest average rating and their average rating value.
   - `get(5)` should return the user(s) with the fifth-highest average rating and their average rating value.
4. **No Ranking Gaps**: If there are multiple users with the same rank (e.g., two users with the highest average rating), the next rank should directly follow without a gap.
5. **Precision**: All `average_rating` calculations should be represented as doubles and formatted to three decimal places in the output.
6. **Report**: In the report, you need to outline:
   - Key problem solving strategy and data structures for the average rating algorithm and the chosen sorting algorithms.
   - The space and time complexity analysis for the average rating algorithm and the chosen sorting algorithms.
   - In addition to the asymptotic analysis, you also need to report empirical comparison of them. That is, run each sorting algorithm 10 times and report the average execution time. Discuss any discrepancies between asymptotic and empirical analyses and provide explanations.


### Component 2: Directed Graph and Trust Path Analysis

For this component, you will implement a graph-based query system. It supports a trust path query feature using Dijkstra's algorithm.

When creating such a directed graph,  each node represents a user. Then, each record in the dataset actually defines a directed edge in the graph. For example, the record `user #6 rated user #2 with 4` is captured by a directed edge from node #6 to node #2, and the edge weight is 4. 

#### Requirements

1. **Graph Construction**: Build a directed graph where each node is a user. Ignore all records with negative ratings. That is, an edge from `SOURCE` to `TARGET` should be created only if the rating is non-negative (Dijkstra's algorithm requires all weights to be non-negative).
2. **checkTrustPath Method**: Implement a function `checkTrustPath(sourceID, targetID)` that:
   - Implements Dijkstra's algorithm to find the shortest trust path from the user with sourceID to targetID in the graph.
   - Prints the total weight of the shortest trust path between the `sourceID` and `targetID` in the first row.
   - Prints the path as a sequence of user IDs separated by commas (e.g., "1, 4, 7, 2").
   - Outputs `"The user [sourceID] does not trust [targetID]."` if no eligible path can be found.
4. **Report**: In the report, you need to outline:
   - How you built the graph and what kind of data structure(s) is used to represent the graph.
   - How Dijkstra's algorithm was implemented and used to find the shortest trust path.
   - Time and space complexity of your graph construction and Dijkstra's algorithm implementation in Big-O notation.




# Task

## Task Deliverables

1.   Source code, which implements at least 4 java files, including 3 for sorting and 1 for graph, is committed and pushed to GitHub Classroom.
2.   A report of about 1,500 words, which explains your solution, is submitted to the Canvas Task 2.

**GitHub Classroom entry**: <https://classroom.github.com/a/jJXjVMy6>



## Task Requirements

### Code 

1.   Code should provide 3 different solutions to sort the records. Name each java file according to the sorting algorithm you use. 
3.   For each algorithm, you can follow the examples of the textbook. However, you cannot just invoke an existing library or implementation.
4.   Each code file should have a main method that can be easily revised to test the relevant methods.




### Report 

The report should explain each algorithm with

*    Key problem solving strategy and data structures
*   *Time complexity* and *space complexity* analysis

For three sorting algorithms, please also report the empirical analysis, and compare with the asymptotic analysis. After the analysis, make recommendations on which sorting algorithm should be used. 
