---
layout: page
title: CSC201 DSA Task 1
---

# Background

# XML

**XML** stands for **EX**tensible **M**arkup **L**anguage. It uses tags to describe data in pure text. Unlike HTML, tags in XML are customly defined. XML was designed to describe data, with focus on what data is.

XML is merely a text-based data description, with information wrapped in tags. The following is an example for XML document:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>
```

# Well-formed XML

An XML document is ***Well Formed*** if it conforms to the syntax rules below.

1.   Start with an ***XML declaration*** to indicate the version and encoding. E.g.

```xml
<?xml version="1.0" encoding=" UTF-8" ?>
```

2.   All open-tags have matching ***close-tags***. E.g. `<from>Jani</from>`
3.   XML tags are ***case sensitive***.

```xml
<Message>This is incorrect</message>
<message>This is correct</message>
<Message>This is correct but a different tag</Message>
```

4.   XML documents must have a ***single root*** element. All other tags are nested inside the root.
5.   XML elements must be ***properly nested***. That is, children tags must close before the parent close tag. E.g. `<b><i>This text is bold and italic</i></b>`

6.   XML attribute values must be ***quoted***. E.g. `<note date="12/11/2007"> … </note>`
7.   Always use ***entity references*** to escape special characters. That is, use `&lt;` for `<`, `&gt;` for `>`, `&amp;` for `&`, `&apos;` for `'`, and `&quot;` for `"`. E.g.

```xml
<message>if salary < 1000 then</message>     <!--- this is incorrect -->

<message>if salary &lt; 1000 then</message>
```

8.   XML comments must be place inside `<!-- … -->`. E.g.

```xml
<!-- This is a comment -->
```

# Task

## Task Deliverables

1.   Source code, which implements an XML checker to verify if an XML document is well-formed, is committed and pushed to GitHub Classroom.

*   A report, which explains your solution, is submitted to the blackboard Task 1.

## Task Requirements

For this assignment, for simplicity:

*   Assume Rule #1, #7, and #8 will not be violated in XML documents. In other words, there is no need to verify these 3 rules.

### Code format

1.   Code should provide 2 different solutions. To be considered as a different solution, the code should apply a different combination of Recursion, Array, LinkedList, Queue, Stack, and Tree.

2.   One solution is named as `XmlCheckerSolutionOne.java`, and another is `XmlCheckerSolutionTwo.java`

3.   Each solution is runnable in the console by taking one parameter for the XML file name, and printing `File xxx is TRUE` if the file is well-formed. Otherwise, println `File xxx is FALSE`. E.g. run the following command:

     ```bash
     java XmlCheckerSolutionOne testFile1.xml
     ```

### Report content

The report should explain each solution with

*    Key problem solving strategy and data structures
*   *Time complexity* and *space complexity* analysis

At then end, make recommendations based on the 2 given solutions.
