---
layout: page
title: CSC201 DSA Task 1 - Grocery Stock Management System Simulation
---

# Grocery Stock Management System Simulation

## 1. Description

In this project, you are tasked with implementing a Grocery Stock Management System that simulates the basic operations of a grocery store such as stocking goods, processing customer orders, discarding expired or spoiled items, applying and ending discounts, handling returns, and calculating total profit or loss. The simulation will read commands from a text file, which describe various operations, and your program must process these commands in the order they appear. The final command in the input will always be a request to compute and report the total profit or loss.

## 2. Grocery Stock Management

### 2.1 List of Commands

This system is a simplified simulation of real world applications. It supports the following commands:

1. `STOCK <item_name> <quantity> <cost_price>`: Add `<quantity>` of `<item_name>` at a unit cost of `<cost_price>` to the inventory. To keep it simple, we don't consider the expiry date of items. In addition, the stocking of an item is not considered as an expense before its disposal as it maintains its value the same as the `<cost_price>`.
2. `ORDER <item_name> <quantity> <sell_price>`: Sell`<quantity>` of `<item_name>` to customers at `<sell_price>` per unit. When fulfilling an order, items added into the inventory earlier should be sold first (FIFO).
3. `EXPIRE <item_name> <quantity>`: Remove `<quantity>` of `<item_name>` from the inventory due to expiry or spoilage. The corresponding cost of acquiring these items is counted as a loss. Items are removed FIFO.
4. `RETURN <item_name> <quantity> <sell_price>`: Process a customer return for `<quantity>` of `<item_name>` previously sold at `<sell_price>`. Returned items are not added back to inventory; the profit from the sale is simply cancelled. If there are multiple sales of `<item_name>` at the same `<sell_price>`, the most recent sale should be reversed first (LIFO by sale).
5. `DISCOUNT <item_name> <discount_percentage>`: Apply a discount of `<discount_percentage>` to all subsequent `ORDER` commands for the specified item. If there are multiple discounts for the same item, only the last `DISCOUNT` is active. The effective price for each ORDER is calculated after applying the active discount in the order that was applied.
6. `DISCOUNT_END <item_name>`: Cancel the most recently applied (last) `DISCOUNT` for the specified item. Only the last matching discount is ended (LIFO for discount removal).
7. `CHECK`: Output the current quantity of each item in inventory.
8. `PROFIT`: Output the total profit or loss so far.

### 2.2 Input Format

The goal is to correctly calculate the profit for a history of operations.

- The input will be a text file where each line represents a command.
- The fields in a command are separated by a single space.
- The second last command in the input file will always be `CHECK`.
- The last command in the input file will always be `PROFIT`.

### 2.3 Output Format

- The output should contain the following:
  - First, list the quantity of each item in inventory, one per line: `<tool_name>: <quantity>`.
  - Then, a single line indicating the total profit or loss: `Profit/Loss: $<amount>`.
  - If the amount is positive, it represents a profit; if negative, a loss.
- If the processing encounters any of the following exceptional situations, output should be `Profit/Loss: NA`.
  - ORDER/EXPIRE more items than the available quantity in inventory.
  - RETURN more items than matching ORDER records at the specified sell price.
  - ORDER items at negative sell price.
  - STOCK items at negative or zero cost.
  - No other exceptional conditions are required to be handled.
- If `Profit/Loss: NA` occurs, there is no need to check or output the correctness of item quantities.

### 2.4 An Example

Assume the input file has the following content:

```
STOCK Apple 100 1.00
ORDER Apple 50 2.00
STOCK Peer 20 1.50
DISCOUNT Apple 10
ORDER Apple 20 2.00
DISCOUNT Apple 5
ORDER Apple 10 2.00
DISCOUNT_END Apple
ORDER Apple 10 2.00
RETURN Apple 5 2.00
EXPIRE Apple 5
CHECK
PROFIT
```

After your program process this input file, it should output the following result:

```
Apple: 9
Peer: 20
Profit/Loss: $74.00
```

`CHECK` outputs 5 apples because: `STOCK` adds 100, all `ORDER` deduct 90, `EXPIRE` deducts 5, `RETURN` does not change the inventory as returned items will not be reused.

Similarly, `CHECK` outputs 20 peers because: `STOCK` adds 20 to the inventory.

The profit is $74.00 because:

`ORDER Apple 50 2.00` command gets profit: 50 * (2.00 - 1.00) = 50.00

`ORDER Apple 20 2.00` command gets profit: 20 * (2.00 * 90% - 1.00) = 16.00. The discount applied is 10%.

The first `ORDER Apple 10 2.00` command gets profit: 10 * (2.00 * 95% - 1.00) = 9.00. The discount applied is 5%.

The second `ORDER Apple 10 2.00` command gets profit: 10 * (2.00 * 90% - 1.00) = 8.00. The discount applied is 10%.

`RETURN Apple 5 2.00` command get profit: -(5 * (2.00 * 90% - 1.00)) = -4.00. This RETURN needs to match the most recent ORDER command(s).

`EXPIRE Apple 5` command get profit: -(5 * 1.00) = -5.00. This RETURN needs to match the earliest  STOCK command(s).

Adding these values up leads to $74.00

## 3. Task

You are going to implement a profit checker to calculate the final profit/loss for a sequence of operations. 

### 3.1 Task Deliverables

1.   Source code, which implements a profit checker to calculate and print the final profit for a given file consisting of operational commands. The code should be committed and pushed to GitHub Classroom.
2.   A report, which explains your solution, is submitted to the Canvas Task 1. 

**GitHub Classroom entry**: <https://classroom.github.com/a/Wb3J9WJA>

### 3.2 Coding Requirements

For this assignment, for simplicity:

*    All monetary amounts should be represented as `double` and formatted to two decimal places in the output.
*   Include a `main` method that processes multiple input files in sequence, printing the profit for each. It then read one input file each time and evaluate all commands in it and output the profit. A list is recommended to store the set of input file names.

### 3.4 Report content

The report should explain your solution with

*    Key problem solving strategy and data structures, and
*   *Time complexity* and *space complexity* analysis

For the complexity analysis, please do at the command level. That is, please explain the complexity of each command. E.g.
`In my implementation, STOCK has the complexity of O(X) where n is the quantity in the command. The reason is ...`

A report template is provided in Task 1 on Canvas for your reference.
