---
layout: page
title: CSC201 DSA Task 1 - Tool Rental System Simulation
---

# Tool Rental System Simulation

## 1. Description

In this project, you are tasked with implementing a Tool Rental System that simulates basic operations of a tool tental shop such as adding tools to inventory, renting tools, returning tools, discarding retired tools, and calculating total profit, including rental incomes and surcharges. The simulation will read commands from a text file, which describe various operations, and your program must process these commands in the order they are read. The final command in the input will always be a request to compute and report the total profit.

## 2. Tool Rental Management

### 2.1 List of Commands

This Tool Rental System is a simplified simulation of real world applications. It supports the following commands:

1. `ADD <tool_name> <quantity> <acquisition_cost>`: Add `<quantity>` of `<tool_name>` at a given `<acquisition_cost>` to the inventory. To keep it simple, we don't consider the depreciation of tools. That is, the purchasing of a tool is not considered as an expense before its disposal as it maintains its value the same as the `<acquisition_cost>`.
2. `RENT <tool_name> <quantity> <rent_fee_per_day> <rent_days>`: Rent `<quantity>` of `<tool_name>` with an associated `<rent_fee_per_day>` per tool for a specified number of <rent_days>. Tools rented are selected with this rule: the tools added into the inventory earlier should be first selected.
3. `RETURN <tool_name> <quantity> <days_rented>`: Return `<quantity>` of `<tool_name>` that were rented for `<days_rented>` days. Returns cancel the earliest rentals first and calculate the rental fee based on the number of days rented. To be specific, there are three possible cases. First, if the actual days are shorter than the plan (`<rent_days>` greater than `<days_rented>`), the rental fee is charged on the actual days (`<days_rented>`). However, there would be a surcharge for the unused days at the cost of 30% of corresponding rental fee. Second, if the actual days equal the plan (`<rent_days>` == `<days_rented>`), the rental fee is charged on the actual days (`<days_rented>`). Third, if the actual days are longer than the plan (`<rent_days>` smaller than `<days_rented>`), the rental fee is charged on the actual days (`<days_rented>`). Moreover, there would be a surcharge for the extra days at the cost of 50% of corresponding rental fee.  
4. `RETURN_DAMAGED <tool_name> <quantity> <replacement_cost>`: `<quantity>` of `<tool_name>` are returned with damages. We simply assume these tools need to be disposed of. Therefoer, the corresponding acquisition cost becomes a loss. Consequently, `<replacement_cost>` per tool is charged to users and no rental fee is calculated in this case. The tools to be removed should be selected with this rule: the items added into the inventory earlier should be first selected. This assumption is not realistic, but will keep the assignment much easier.
5. `DISCARD <tool_name> <quantity>`: Remove `<quantity>` of `<tool_name>` from the inventory and the corresponding cost of acquiring these items are marked as a loss. The items to be removed should be selected with this rule: the items added into the inventory earlier should be first selected.
6. `CHECK`: Output the current quantity of each tool.
7. `PROFIT`: Output the business total profit, which equals `(total incomes - total expenses)`.

### 2.2 Input Format

The goal is to correctly calculate the profit for a history of operations.

- The input will be a text file where each line represents a command.
- The fields in a command are separated by a single space.
- The second last command in the input file will always be `CHECK`.
- The last command in the input file will always be `PROFIT`.

### 2.3 Output Format

- The output should contain the following content:
  - First list the quantity of each item in the inventory line by line, formatted as `<tool_name>: <quantity>`.
  - Then a single line indicating the total profit or loss, formatted as `Profit/Loss: $<amount>`.
  - If the amount is positive, it represents a profit; if negative, it represents a loss.
- If the processing encounters either of the following unexpected situations, output should be `Profit/Loss: NA`.
  - RENT/DISCARD more items than the available quantity in the inventory, 
  - RETURN/RETURN_DAMAGED commands <span style="color:red">have higher `<quantity>` than the available RENT records.</span>
  - RENT items at negative prices.
  - RETURN_DAMAGED has a negative replacement cost.
  - No other exceptional conditions are required to be handled.
- If `Profit/Loss: NA`, there's no need to check the correctness of numbers of tools.

### 2.4 An Example

Assume the input file has the following content:

```
ADD Drill 10 50.00
ADD Saw 5 75.00
RENT Drill 3 5.00 7
RENT Saw 2 7.00 10
RETURN Drill 2 7
RETURN Saw 1 15
RETURN_DAMAGED Drill 1 60.00
DISCARD Saw 1
CHECK
PROFIT
```

After your program process this input file, it should output the following result:

```
Drill: 9
Saw: 3
Profit/Loss: $92.50
```

`CHECK` outputs 9 Drills because: `ADD` adds 10, `RENT` deducts 3, `RETURN` adds 2, `RETURN_DAMAGED` does not change the inventory as it in fact adds 1 back to the inventory but then discards it.

Similary, `CHECK` outputs 3 Saws because: `ADD` adds 5, `RENT` deducts 2, `RETURN` adds 1, `DISCARD` deducts 1 from the inventory.

The profit is $65 because:

`RETURN Drill 2 7` command gets profit [rentals + surcharge]: 2 * 5.0 * 7 + 0 = 70.00

`RETURN Saw 1 15` command get profit [rentals + surcharge]: (1 * 7.0 * 10) + (1 * (7.0 * 50%) * (15-10) ) = 87.50

`RETURN_DAMAGED` command get profit [replacement_cost - acquisition_cost]: 1 * (60.0 - 50.0) = 10.00

`DISCARD` command get profit [-acquisition_cost]: -75.0 = -75.0

## 3. Task

You are going to implement a profit checker to calculate the final profit/loss for a sequence of operations. 

### 3.1 Task Deliverables

1.   Source code, which implements a profit checker to calculate and print the final profit for a given file consisting of operational commands. The code should be committed and pushed to GitHub Classroom.
2.   A report, which explains your solution, is submitted to the Canvas Task 1. 

**GitHub Classroom entry**: <https://classroom.github.com/a/1QgDaAmI>

*   Some test files are provided in the root folder of the starter repository.

### 3.2 Coding Requirements

For this assignment, for simplicity:

*    All monetary amounts should be represented as `double` and formatted to two decimal places in the output.
*   Include a `main` method that contains a list which stores a list of string names for multiple input files. It then read one input file each time and evaluate all commands in it and output the profit.

### 3.4 Report content

The report should explain your solution with

*    Key problem solving strategy and data structures, and
*   *Time complexity* and *space complexity* analysis

<span style="color:red">For the complexity analysis, please do at the command level. That is, please explain the complexity of each command.</span> E.g.
`In my implementation, ADD has the complexity of O(n) where n is the quantity in the command. The reason is ...`

A report template is provided in Task 1 on Canvas for your reference.
