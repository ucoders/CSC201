---
layout: page
title: CSC201 DSA Task 1 - Inventory Management System Simulation
---

# Inventory Management System Simulation

## 1. Description

In this project, you are tasked with implementing an Inventory Management System that simulates basic operations of a business such as adding items to inventory, selling items, handling returned items, donating items, writing off damaged or lost items, and calculating the profit or loss of the business. The simulation will read commands from a text file, which describe various operations, and your program must process these commands in the order they are read. The final command in the input will always be a request to compute and report the total profit or loss.

## 2. Inventory management

### 2.1 List of Commands

This Inventory Management System supports the following commands:

1. `ADD <item_name> <quantity> <price>`: Add `<quantity>` of `<item_name>` at a given `<price>` to the inventory.
2. `SELL <item_name> <quantity> <price>`: Sell `<quantity>` of `<item_name>` from the inventory at the given `<price>`. These sold items are chosen with this rule: the items added into the inventory earlier should be first selected.
3. `WRITEOFF <item_name> <quantity>`: Remove `<quantity>` of `<item_name>` from the inventory and the corresponding cost of acquiring these items are marked as loss. The items to be removed should be selected with this rule: the items added into the inventory earlier should be first selected.
4. `DONATE <item_name> <quantity>`: Remove `<quantity>` of `<item_name>` from the inventory as a donation. We simply assume donations have no impact on the profit/loss calculation. The items to be removed should be selected with this rule: the items added into the inventory earlier should be first selected.
5. `RETURN <item_name> <quantity> <price>`: Simulate the return of `<quantity>` of `<item_name>` that were sold at `<price>` each. To simplify the simulation, the returned items will not be added back to the inventory for future reselling. It only cancels its corresponding selling profit but has no impact on the future inventory. <span style="color:red">If there are multiple sales of `<item_name>` at the same `<price>`, then the most recent sale should be the first to be cancelled. If no such sales record exists for the given `<item_name>` and `<price>`, or if the quantity in such a sales record is less than the `<quantity>` to be returned, then the output should be `Profit/Loss: NA`.</span>
6. `CHECK`: Output the current quantity of each item.
7. `PROFIT`: Calculate and output the total profit or loss so far.

### 2.2 Input Format

The goal is to correctly calculate the profit for a history of operations.

- The input will be a text file where each line represents a command.
- The fields in a command are separated by a single space.
- The second last command in the input file will always be `CHECK`.
- The last command in the input file will always be `PROFIT`.

### 2.3 Output Format

- The output should contain the following content:
  - First list the quantity of each item in the inventory line by line, formatted as `<item_name>: <quantity>`.
  - Then a single line indicating the total profit or loss, formatted as `Profit/Loss: $<amount>`.
- If the amount is positive, it represents a profit; if negative, it represents a loss.
- If the processing encounter either of the following unexpected situations, output should be `Profit/Loss: NA`.
  - SELL/DONATE/WRITEOFF more items than the available quantity in the inventory, 
  - For RETURN commands, <span style="color:red">if no such sales record exists for the given `<item_name>` and `<price>`, or if the quantity in such a sales record is less than the `<quantity>` to be returned.</span>
  - SELL items at negative prices.
  - If `Profit/Loss: NA`, there's no need to check the correctness of numbers of items.

### 2.4 An Example

Assume the input file has the following content:

```
ADD Apple 100 1.20
SELL Apple 50 1.50
RETURN Apple 5 1.50
DONATE Apple 5
WRITEOFF Apple 2
CHECK
PROFIT
```

After your program process this input file, it should output the following result:

```
Apple: 43
Profit/Loss: $11.10
```

`CHECK` outputs 45 Apple because: `SELL` deducts 50, `RETURN` does not change the inventory, `DONATE` deducts 5, and `WRITEOFF` deducts 2.

The profit is $11.1 because:

`SELL` command gets profit: 50 * (1.50 - 1.20) = 15.00

`RETURN` command get profit: -5 * (1.50 - 1.20) = -1.50

`DONATE` command get profit: 5 * 0 = 0.00

`WRITEOFF` command get profit: -2 * 1.20 = -2.40

## 3. Task

You are going to implement a profit checker to calculate the final profit/loss for a sequence of operations. 

### 3.1 Task Deliverables

1.   Source code, which implements a profit checker to calculate and print the final profit for a given file consisting of operational commands. The code should be committed and pushed to GitHub Classroom.
2.   A report, which explains your solution, is submitted to the Canvas Task 1. 

**GitHub Classroom entry**: <https://classroom.github.com/a/F_1PGGfz>

*   Some test files are provided in the root folder of the starter repository.

### 3.2 Coding Requirements

For this assignment, for simplicity:

*    All monetary amounts should be represented as `double` and formatted to two decimal places in the output.
*   Include a `main` method that contains a list which stores a list of string names for multiple input files. It then read one input file each time and evaluate all commands in it and output the profit.


### 3.4 Report content

The report should explain your solution with

*    Key problem solving strategy and data structures, and
*   *Time complexity* and *space complexity* analysis

A report template is provided in Task 1 on Canvas for your reference.
