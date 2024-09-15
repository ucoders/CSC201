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

This indicates that the hero with `id1` and the hero with `id2` appeared together in one Marvel comic issue.

The data is available in the starter code once your initiate the project in the GitHub classroom. The original data source is from <https://www.kaggle.com/datasets/csanhueza/the-marvel-universe-social-network>

The objective of this project is to develop a query system for the hero network. Three key components are required. 

### Task 1: Counting and Sorting Co-occurrences

#### 1.1 Remove Duplicated Records

Since a pair `id1,id2` represents a co-occurrence relation, its reverse pair `id2,id1` should be considered equivalent. For this project, we need to first remove duplicated records, including reverse pairs. 

*   Process `hero-network.csv` and remove all duplicated and reverse pairs.
*   Save the result into a CSV file named `hero-network-nodup.csv`.

#### 1.2 Count and Sort Heroes by Co-occurrences

With the de-duplicated dataset, we can calculate the frequency of co-occurrences for each hero. 

-   Count how many times each hero (ID) co-appears with other heroes in the dataset `hero-network-nodup.csv`.
-   Sort all heroes first by the count of their co-occurrences (in descending order), then by their ID (in ascending order).
-   Save the sorted result into a CSV file named `sorted_heroes.csv`, where each record is in the form `id,count`, representing the number of times the hero with `id` co-appears with others.

#### 1.3 Query Co-occurrence Rank

With the sorted co-occurrences, we can answer queries about the popularity of heroes.

-   Implement a function `void getRank(int n)` that prints all hero IDs with the $n^{th}$ highest number of co-occurrences.
    -   Example: "Who has the 5th highest co-occurrence?"



#### Requirements

1. **Source code file**: Implement all 3 subtasks in `CoOccurrence.java`. You can create auxilary classes (e.g., for sorting algorithm implementation), but they must be invoked from `CoOccurrence.java` to perform the tasks.

2. **Get Method**: The `getRank(int n)` method should print how many IDs are at this rank, and then print all these IDs. 

    - `get(1)` should print the total number and the hero(es) with the highest co-occurrences.
    - `get(5)` should print the total number and the hero(es) with the fifth-highest co-occurrences.

4. **No Ranking Gaps**: All ranks are incremented by 1. Even if multiple heroes share the same rank `k` (e.g., three heroes with the highest co-occurrences), the next rank should simply be `k+1` without any gaps.

4. **Report**: Your report should outline:

    - Key problem solving strategies and data structures used for each task.
    - Time and space complexity analysis for each task.

    


### Task 2: Graph Traversal and Degree of Separation

Using the co-occurrence data from `hero-network-nodup.csv`, construct a graph where each hero is a node, and an edge exists between two nodes if the corresponding heroes co-appeared in a comic.

This task will address queries about the Degree of Separation between two heroes.

**Definition:** The ***Degree of Separation*** between two heroes is the shortest number of edges (hops) connecting them in the graph.

#### 2.1 Degree of Separation between Two Heroes

Implement a function `void getDegreeOfSeparation(int id1, int id2)` that prints the Degree of Separation between `id1` and `id2`.

-   If `id1 == id2`, the degree is 0.
-   If `id1` and `id2` are not reachable, the degree is -1.
-   Otherwise, it's a positive integer.

#### 2.2 Nodes at a Given Degree of Separation

Implement a function `void getHeroesOfDegree(int id, int degree)` that prints the total number of heroes exactly `degree` separation away from `id`.



#### Requirements

1. **Source code file**: Implement both subtasks in `SeparationDegree.java`. You can create auxilary classes, but they must be invoked from `SeparationDegree.java` to perform the tasks.

2. **Report**: Your report should outline:
    - Key problem solving strategies and data structures used for each task.
    - Time and space complexity analysis for each task.




### Task 3: Weighted Shortest Path

In this task, you will assign a weight to each edge in the graph based on the properties of the connected nodes.

**Definition:** The ***weight*** of an edge connecting `node1` and `node2` is defined as the minimum of the degrees (number of connections) of `node1` and `node2`. Note that degree here refers to the number of edges connected to a node, which is different from "Degree of Separation". 

#### 3.1 Shortest Path between Two Heroes

With the weighted graph constructed, implement a function `void getShortestPath(int id1, int id2)` that prints the shortest path between `id1` and `id2`. The output should include:

-   -   The total weight of the shortest path.
    -   The number of hops (edges) in the path.
    -   The sequence of node IDs along the path, separated by commas (e.g., "1, 4, 7, 2").
    -   If no path is found, output: `"The heroes [id1] and [id2] are not reachable."` .



#### Requirements

1. **Source code file**: Implement the task in `ShortestPath.java`. You can create auxilary classes, but they must be invoked from `ShortestPath.java` to perform the task.
4. **Report**: Your report should outline:
   - Key problem solving strategies and data structures used for the task.
   - Time and space complexity analysis for the task.




# Task

## Task Deliverables

1.   Commit and push your source code to GitHub CLassroom, including at least 3 java files.
2.   Submit a report of about 1,500 words, explaining your solution to each task, via Canvas Task 2.

**GitHub Classroom entry**: <https://classroom.github.com/a/aOfPNfEk>



## General Guideline

### Code

1.   You may use existing data structures from the standard Java, Kotlin, or Python SDK. Otherwise, you will need to implement your own.
2.   All algorithms must be implemented by you, though you may refer to textbook examples.
3.   Each code file should have a `main` method that allows easy testing of the relevant methods.

