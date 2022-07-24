---
layout: page
title: CSC201 DSA
---

# Learning outcomes

1.   Get familiar with the overall plan of the semester
2.   Review the usage of Java



# Readings

*   Chapter 1 & 2 of the textbook



# Workshop: Java Practice


## Discussion

* **[R-2.9]** What are some potential efficiency disadvantages of having very deep inheritance trees, that is, a large set of classes, A, B, C, and so on, such that B extends A, C extends B, D extends C, etc.?



* **[R-2.10]** What are some potential efficiency disadvantages of having very shallow inheritance trees, that is, a large set of classes, A, B, C, and so on, such that all of these classes extend a single class, Z?



* **[R-2.11]** Consider the following code fragment, taken from some package:

```java
public class Maryland extends State {
    Maryland( ) { /* null constructor */ } 
    public void printMe( ) { System.out.println("Read it."); } 
    
    public static void main(String[ ] args) {
        Region east = new State( );
        State md = new Maryland( );
        Object obj = new Place( );
        Place usa = new Region( );
        md.printMe( );
        east.printMe( );
        ((Place) obj).printMe( );
        obj = md;
        ((Maryland) obj).printMe( );
        obj = usa;
        ((Place) obj).printMe( );
        usa = md;
        ((Place) usa).printMe( );
    }
}

class State extends Region {
    State( ) { /* null constructor */ }
    public void printMe( ) { System.out.println("Ship it."); }
}

class Region extends Place {
    Region( ) { /* null constructor */ }
    public void printMe( ) { System.out.println("Box it."); }
}

class Place extends Object {
    Place( ) { /* null constructor */ }
    public void printMe( ) { System.out.println("Buy it."); }
}
```

What is the output from calling the `main( )` method of the `Maryland` class?



* **[R-2.13]** Consider the following inheritance of classes: 

    * Class `Goat` extends `Object` and adds an instance variable `tail` and methods `milk( )` and `jump( )`.
    * Class `Pig` extends `Object` and adds an instance variable `nose` and methods `eat(food)` and `wallow( )`.
    * Class `Horse` extends `Object` and adds instance variables`height` and `color`, and methods `run( )` and `jump( )`.
    * Class `Racer` extends `Horse` and adds a method `race( )`.
    * Class `Equestrian` extends `Horse` and adds instance variable `weight` and `isTrained`, and methods `trot( )` and `isTrained( )`.

    Let `d` be an object variable of type `Horse`. If `d` refers to an actual object of type `Equestrian`, can it be cast to the class `Racer`? Why or why not?

    

##  Implementation

* **[C-1.20]*** Write a Java method that 1) creates an integer array of 100 items which are randomly selected between 1 and 1000, and 2) determines if all the numbers are different from each other (that is, they are distinct).



* **[C-1.22]** Write a short Java program that outputs all possible strings formed by using the characters 'c', 'a', 't', 'd', 'o', and 'g' exactly once.



* **[C-2.28]** Write a set of Java classes that can simulate an Internet application in which one party, Alice, is periodically creating a set of packets that she wants to send to Bob. An Internet process is continually checking if Alice has any packets to send, and if so, it delivers them to Bob’s computer; Bob is periodically checking if his computer has a packet from Alice, and if so, he reads and deletes it.



* **[P-2.35]** Write a Java program that inputs a list of words, separated by whitespace, and outputs how many times each word appears in the list. You need not worry about efficiency at this point, however, as this topic is something that will be addressed later in this book.

