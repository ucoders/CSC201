---
layout: page
title: CSC201 DSA Task 2
---

# Background

Wikipedia is a free encyclopaedia written collaboratively by volunteers around the world. A small part of Wikipedia contributors are ***administrators***, who are users with access to additional technical features that aid in maintenance. In order for a user to become an administrator, a *Request for adminship* (RfA) is issued and the Wikipedia community via a public discussion or a vote decides who to promote to adminship. 

The dataset for the assignment was Wikipedia voting on promotion to administratorship. One record/row represents a directed edge A->B which means user A voted on B becoming Wikipedia administrator. For example, in the following record, user 30 voted user 1412 becoming an administrator.

| FromNodeId | ToNodeId |
| ---------- | -------- |
| 30         | 1412     |



The data is available in the starter code once your initiate the project in the Gitub classroom. The original data source is from <https://snap.stanford.edu/data/wiki-Vote.html>

A key requirement is to rank applicants by the votes they received. It's your responsibility to implement a simple query system for the data set. The required functionality includes:

1.    Implement `VoteCounter.java`, which 
     * Reads the data source file and count the number of votes for each user
     * Outputs the voting counts into `Vote-Results.csv` in which each row includes 2 fields: UserID,VoteCount. Please keep in mind this csv file should not be sorted by VoteCount.
     * In the report, you need to explain how you do the counting, along with the space and time complexity analysis in bigO notation.
2.   Based on `Vote-Results.csv`, implement a method `get(int rank)` which, for the user winning the given ranking order, prints the voting results for that user, including the userID and the total votes received. For example, `get(2)` will print the voting information for the user who wins the second highest votes, and `get(5)` will print the voting information for the user who wins the fifth highest votes. 
     * `get()` should be based on the sorted column. Therefore, you need to sort the data set based on the VoteCount first. 
     * You're requested to implement ***3 different sorting methods***, and name the code files with the corresponding sorting method name, eg. `MergeSort.java`. 
     * Inside each sorting implementation, provide a `get()` method so that it's easier to support the users' needs.
     * In the report, you need to explain 3 different sort methods along with the space and time complexity analysis. In addition to the asymptotic analysis, you also need to report empirical comparison of them. That is, record the actual execution time for sorting process. You can run each sorting algorithm 10 times and report the average value. If there's any mismatch between the asymptotic and empirical analysis, please give a reasonable explanation.

# Task

## Task Deliverables

1.   Source code, which implements 4 java files, is committed and pushed to GitHub Classroom.
2.   A report of about 1,500 words, which explains your solution, is submitted to the Canvas Task 2.

**GitHub Classroom entry**: <https://classroom.github.com/a/h4TUztIM>



## Task Requirements

### Code 

1.   Code should also provide `VoteCounter.java` for counting the votes for each user.
2.   Code should provide 3 different solutions to sort the records. Name each java file according to the sorting algorithm you use. 
3.   For each algorithm, you can follow the examples of the textbook. However, you cannot just invoke an existing library or implementation.
4.   Each code file should have a main method that can be easily revised to test the relevant methods.




### Report 

The report should explain each algorithm with

*    Key problem solving strategy and data structures
*   *Time complexity* and *space complexity* analysis

For three sorting algorithms, please also report the empirical analysis, and compare with the asymptotic analysis. After the analysis, make recommendations on which sorting algorithm should be used. 
