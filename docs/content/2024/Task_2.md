---
layout: page
title: CSC201 DSA Task 2
---

# Background

Marvel Comics has a rich history of publishing iconic comic books since its early days as Timely Comics. The **Marvel Universe** is a vast, fictional shared universe where many of Marvel’s most famous stories unfold. It is home to legendary superhero teams such as the Avengers, the X-Men, the Fantastic Four, and the Guardians of the Galaxy, as well as countless individual superheroes. These characters often appear together in crossovers, forming intricate connections and relationships that span across various comic book titles, movies, and other media. This interconnected world is a hallmark of Marvel’s storytelling, creating a cohesive universe where heroes and villains interact in dynamic ways.

In this assignment, you will work with a dataset derived from the **Marvel Universe Social Network**, where each node represents a Marvel hero, and an edge between two nodes indicates that the heroes appeared together in the same comic issue. Two data files are provided:

*   `hero-network.csv`, which is the dataset we will work with. The dataset has been anonymised, and hero names are replaced with unique numeric IDs. Each row in the dataset consists of two IDs, representing a co-occurrence between the two corresponding heroes.
*   `hero-network-ids.csv`, which shows the mapping between hero names and their IDs. This file is provided just for your curiosity about who is who.

The hero network dataset is provided as a CSV file, where each row is in the format:

```
id1,id2
```

This indicates that hero with `id1` and hero with `id2` appeared together in one Marvel comic issue.

The data is available in the starter code once your initiate the project in the GitHub classroom. The original data source is from <https://www.kaggle.com/datasets/csanhueza/the-marvel-universe-social-network>

The objective of this project is to develop a query system for the hero networks. There are three key components are required. 

### Task 1: Counting and Sorting Co-occurrences

#### 1.1 Remove Duplicated Records

As a pair `id1,id2` represents the co-occurrence relation, its reverse pair `id2,id1` should be considered as equivalent. For the purpose of this project, we need to first remove duplicated records, including duplicated pairs and reverse pairs. 

*   Process `hero-network.csv` and remove all duplicated pairs and reverse pairs.
*   Save the result into a CSV file named `hero-network-nodup.csv`.

#### 1.2 Count and Sort Heroes by Co-occurrences

With the dataset without duplication, we can calculate the frequency of co-occurrences for heros. 

-   Count how many times each hero (ID) co-appears with other heroes in the dataset `hero-network-nodup.csv`.
-   Sort all heroes first by the count of their co-occurrences (in descending order), then by their ID (in ascending order).
-   Save the sorted result into a CSV file named `sorted_heroes.csv`, with each record in the form of `id,count`, representing the hero with `id` co-appears with `count` other heroes.

#### 1.3 Query Co-occurrence Rank

With the sorted co-occurrences, we can answer the queries about the popularity of heroes.

-   Implement a function `void getRank(int n)` that prints all hero IDs with the $n^{th}$ highest number of co-occurrences.
    -   Example: "Who has the 5th highest occurrence?"



#### Requirements

1. **Source code file**: Implement all 3 subtasks in `CoOccurrence.java`. You can create auxilary classes, e.g. sorting algorithm implementation. But they'll be invoked in `CoOccurrence.java` to perform the tasks.

2. **Get Method**: The method `getRank(int n)` first prints how many IDs are at this rank, and then prints all these IDs. 

    - `get(1)` should print the total number and the user(s) with the highest co-occurrences.
    - `get(5)` should print the total number and the user(s) with the fifth-highest co-occurrences.

4. **No Ranking Gaps**: All ranks are incremental by 1. Even if there are multiple users with the same rank `k` (e.g., three users with the highest co-occurrences), the next rank should simply be `k+1` without a gap.

4. **Report**: In the report, you need to outline:

    - Key problem solving strategy and data structures for each task solution.
    - The space and time complexity analysis for each task solution.

    


### Task 2: Graph Traversal and Degree of Separation

Using the co-occurrence data `hero-network-nodup.csv`, construct a graph where each hero is a node, and an edge exists between two nodes if the corresponding heroes co-appeared in a comic.

This task answers the queries about the Degree of Separation between two heroes.

**Definition:** Degree of Separation between two heroes is the shortest number of edges (hops) connecting them in the graph.

#### 2.1 Degree of Separation for Two Heroes

With the graph constructed, we can answer the queries about the Degree of Separation between heroes.

-   Implement a function `void getDegreeOfSeparation(int id1, int id2)` that prints the Degree of Separation between `id1` and `id2`.
    -   If `id1 == id2`, the degree is 0.
    -   If `id1` and `id2` are not reachable, the degree is -1.
    -   Otherwise, it's a positive integer.

#### 2.2 Nodes with a Given Degree of Separation

With the graph constructed, we can also answer the queries about the heroes with a given Degree of Separation.

*   Implement a function `void getHeroesOfDegree(int id, int degree)` that prints the total number of heroes that are exactly with `degree` separation away from `id`.



#### Requirements

1. **Source code file**: Implement both subtasks in `SeparationDegree.java`. You can create auxilary classes, but they'll be invoked in `SeparationDegree.java` to perform the tasks.

2. **Report**: In the report, you need to outline:
    - Key problem solving strategy and data structures for each task solution.
    - The space and time complexity analysis for each task solution.




### Task 3: Weighted Shortest Path

In this task, you will assign a weight to each edge in the graph based on the properties of the connected nodes.

*   **Definition:** The ***weight*** of an edge connecting `node1` and `node2` is defined as the minimum of the degrees (number of connections) of `node1` and `node2`. Beware the meaning of degree here is the number of edges connected to a node. It's different from "Degree of Separation". 

#### 3.1 Shortest Path between Two Heroes

With the weighted graph constructed, we can answer the queries about the shortest path between heroes.

-   Implement a function `void getShortestPath(int id1, int id2)` that prints the shortest path between `id1` and `id2`. The output should include:
    -   The total weight of the shortest path.
    -   The length of the shortest path, which is the number of hops between them.
    -   The sequence of node IDs along the path, separated by commas (e.g., "1, 4, 7, 2").
    -   Outputs `"The heroes [id1] and [id2] are not reachable."` if no eligible path can be found.



#### Requirements

1. **Source code file**: Implement the task in `ShortestPath.java`. You can create auxilary classes, but they'll be invoked in `ShortestPath.java` to perform the task.
4. **Report**: In the report, you need to outline:
   - Key problem solving strategy and data structures for the task solution.
   - The space and time complexity analysis for the task solution.




# Task

## Task Deliverables

1.   Source code, which implements at least 3 java files, is committed and pushed to GitHub Classroom.
2.   A report of about 1,500 words, which explains your solution, is submitted to the Canvas Task 2.

**GitHub Classroom entry**: <https://classroom.github.com/a/aOfPNfEk>



## General Guideline

### Code

1.   For data structures, you can use existing implementations included in the standard Java, Kotlin, or Python SDK. Otherwise, you need to implement your own.
2.   For algorithms, you need to implement your own. Your implementation may follow the examples in the textbook.
3.   Each code file should have a main method that can be easily revised to test the relevant methods.


