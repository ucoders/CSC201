---
layout: page
title: CSC201 DSA Task 2
---

# Background

Your company received a data set about the historical records of passenger flights between Australian airports. The schema of the table and a sample record are shown below.

| City1    | City2         | Month  | Passenger_Trips | Aircraft_Trips | Passenger_Load_Factor | Distance_GC_(km) | RPKs     | ASKs     | Seats | Year | Month_num |
| -------- | ------------- | ------ | --------------- | -------------- | --------------------- | ---------------- | -------- | -------- | ----- | ---- | --------- |
| ADELAIDE | ALICE SPRINGS | Jan-84 | 15743           | 143            | 81.8                  | 1316             | 20717788 | 25327369 | 19246 | 1984 | 1         |

The attributes of the data have the following patterns:

*   `City1` and `City2` in a record represents a flight route between these two cities, including both directions.
*   The flight details are aggregated by months. `Month` is split into 2 fields: `Year` and `Month_num` for easier processing.
*   `Aircraft_Trips` is the total number of flights between two cities.
*   `Seats` represents the total number of available passenger seats for all flights in a given month between two cities.
*   `Passenger_Trips` represents the sold number of passenger seats for all flights in a given month between two cities.
*   `Passenger_Load_Factor` equals to `Passenger_Trips/Seats`.
*   `Distance_GC_(km)` is great circle distance between two airports (connected to city).
*   `ASKs` is Available Seat Kilometres. It equals to `Seats * Distance\_GC\_(km)`.
*   `RPKs` is Revenue Passenger Kilometres. It equals to `ASKs * Passenger_Load_Factor`.

The data is available in the starter code once your initiate the project in the Gitub classroom. The original data source is from <https://data.gov.au/dataset/ds-dga-c5029f2a-39b3-4aef-8ae1-73e7962f6170>

Now, it's your responsibility to implement a simple query system for the data set. The required funcationality includes:

1.   `Passenger_Load_Factor` is an important measurement for profitability of a flight and users like to find flight records with high factor values. Therefore, you need to implement a method `get(int rank)` which returns the flight record(s) with the given ranking order. For example, `get(1)` will return the record(s) with the highest load factor, and `get(5)` will return the record(s) with the fifth highest load factor. 
     *   `get()` should be based on the sorted column. Therefore, you need to sort the data set based on the load factor first. 
     *   You're requested to implement 3 different sorting methods, and name the code files with the corresponding sorting method name, eg. `MergeSort.java`. 
     *   Inside each sorting implementation, provide a `get()` method so that it's easier to support the users' needs.
     *   If you want to apply bucket sort, you need to first turn decimal values into integer values. A simple trick here is to multiple 10 by the load factor.
     *   In the report, you need to explain 3 different sort methods along with the space and time complexity analysis. In addition to the asymptotic analysis, you also need to report empirical comparison of them. That is, record the actual execution time for sorting process. You can run each sorting algorithm 10 times and report the average value. If there's any mismatch between the asymptotic and empirical analysis, please give a reasonable explanation.
2.   A common inquiry from customers is if we can find an itinerary between two cities. Based on the data set, if we join `City1` and `City2` of different records, we can discover the flight networks across Australia, thus answering users' queries. To make the task easier, let's just consider December 2018. 
     *   You need to manually extract December 2018 records from the original data set and save them as flights_201812.csv. You can use Excel or any tool.
     *   Implement `ItineraryExplorer.java`, which
         *   Use the extracted records to build a graph of flights.
         *   Provide a function `String checkItinerary(String city1, String city2)` which will output the shortest flight path between two cities, e.g. "city1, city4, city7, city2". If no eligible path can be found, just output `"These 2 cities are not connected."`
         *   In the report, you need to explain how you build the graph and how to find the shortest path, along with the space and time complexity analysis in bigO notation.

# Task

## Task Deliverables

1.   Source code, which implements 4 java files, is committed and pushed to GitHub Classroom.
2.   A report of about 1,500 words, which explains your solution, is submitted to the blackboard Task 2.

**GitHub Classroom entry**: <https://classroom.github.com/a/7eg31Nfc>



## Task Requirements

### Code 

1.   Code should provide 3 different solutions to sort the records. Name each java file according to the sorting algorithm you use. 
2.   Code should also provide ItineraryExplorer.java for checking itineraries between cities.
3.   For each algorithm, you can follow the examples of the textbook. However, you cannot just invoke an existing library or implementation.
4.   Each code file should have a main method that can be easily revised to test the relevant methods.




### Report 

The report should explain each algorithm with

*    Key problem solving strategy and data structures
*   *Time complexity* and *space complexity* analysis

For three sorting algorithms, please also report the emperical analysis, and compare with the asymptotic analysis. After the analysis, make recommendations on which sorting algorithm should be used. 
