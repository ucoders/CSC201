---
layout: page
title: CSC201 DSA Task 1
---

# Background

*Credit: Part of the content about JSON is derived from: <https://www.w3schools.com/js/js_json_syntax.asp>*

# JSON

**JSON** stands for **J**ava**S**cript **O**bject **N**otation. It uses key/value pairs to describe data in pure text and becomes the most popular format of online data exchange. The JSON syntax is a subset of the JavaScript syntax.

The following is an example for JSON data. It describes an object with a $note$ field, which is in turn an object with 5 member fields, including $to$, $from$, $heading$, $length$, and $body$.

```json
{
    "note": {
        "to": "Tove",
        "from": "Jani",
        "heading": "Reminder",
        "length": 20,
        "body": "do not forget me this weekend!"
    }
}
```

# JSON Syntax Rules

JSON syntax is derived from JavaScript object notation syntax.

1.   Data is in key/value pairs

A data entry in JSON is written as key/value pairs. A key/value pair consists of a field name (in double quotes), followed by a colon, followed by a value. For example:

```json
"to": "Tove"
```

It should be noted that keys in JSON must be strings, and require ***double quotes***.

*Values* must be one of the following data types:

-   a string, again must be written with ***double quotes***
-   a number
-   an object, which is surrounded by { }
-   an array, which is surrounded by [ ]
-   a boolean, either $true$ or $false$
-   null



2.   Data is separated by commas

3.   Curly braces hold objects. For example, the following is a simple object with 2 fields:

```json
{
    "id": "123456",
    "name": "Jani"
}
```

4.   Square brackets hold arrays. In JSON, array values must be of type string, number, object, array, boolean or null. It should be noted that in JavaScript, the elements of an array can have different types. For example, the following is an array with 5 elements, a string, a null, an object with only one field, a number, and an array with 1 element.

```json
["test", null, {"name": "Jani"}, 5, [1]]
```

More detailed explanations and examples can be found on W3School website: <https://www.w3schools.com/js/js_json_intro.asp>



Based on the description above, it is clear that a valid JSON representation should satisfy:

#5.   XML elements must be ***properly nested***. That is, children tags must close before the parent close tag. E.g. `<b><i>This text is bold and italic</i></b>`

# Task

You are going to write a validator for JSON files to check if they are sound in syntax regarding the rules described earlier. A key challenge in this task is to ensure objects and arrays are ***properly nested***. That is, children objects/arrays must close before the parent close. E.g. `{ [ some thing here ] }` is valid but `{ [ some thing here } ]` is not.

## Task Deliverables

1.   Source code, which implements a JSON checker to verify if a JSON document is syntactically sound, is committed and pushed to GitHub Classroom.
2.   A report, which explains your solution, is submitted to the Canvas Task 1. 

**GitHub Classroom entry**: <https://classroom.github.com/a/XlRFNkHz>

*   Some test json files are provided in the root folder of the starter repository.

## Task Requirements

For this assignment, for simplicity:

*   Only assume the rules listed at the beginning of this instruction file. There's no need to consider names or strings with special  characters. 
*   Assume the value of a key has only 3 possibilities: string, array, object. There will be no numbers, booleans, or null.

### Code format

1.   Code should provide 2 different solutions. To be considered as a different solution, the code should apply a different combination of Recursion, Array, LinkedList, Queue, Stack, and Tree.

2.   One solution is named as `JSONCheckerSolutionOne.java`, and another is `JSONCheckerSolutionTwo.java`

3.   For each solution, it should contain a String array variable which stores a collection of JSON file names, and your code will iterate through this array and check the validly of each file. For each file, print `File xxx is Valid` or  `File xxx is INValid` according to the verification.


### Report content

The report should explain each solution with

*    Key problem solving strategy and data structures
*   *Time complexity* and *space complexity* analysis

At the end, make recommendations based on the 2 given solutions.

A report template is provided in Task 1 on Canvas for your reference.
