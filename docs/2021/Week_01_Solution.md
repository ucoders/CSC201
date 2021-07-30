# Workshop 1 Hints and Solutions

## Discussion

* **[R-2.9]** What are some potential efficiency disadvantages of having very deep inheritance trees, that is, a large set of classes, A, B, C, and so on, such that B extends A, C extends B, D extends C, etc.?

**[Hint]** Think about what happens when a new instance of class Z is created and when methods of class Z are called.

**[Solution]** There are two immediate inefficiencies: (1) the chaining of constructors implies a potentially long set of method calls any time an instance of a deep class, Z, is created, and (2) the dynamic dispatch algorithm for determining which version of a certain method to use could end up looking through a large number of classes before it finds the right one to use.



* **[R-2.10]** What are some potential efficiency disadvantages of having very shallow inheritance trees, that is, a large set of classes, A, B, C, and so on, such that all of these classes extend a single class, Z?

**[Hint]** Think about code reuse.

**[Solution]** Whenever a large number of classes all extend from a single class, it is likely that you are missing out on potential code reuse from similar methods in different classes. There is likely some factoring of methods into common classes that could be done in this case, which would save programmer time and maintenance time, by eliminating duplicated code.



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

**[Hint]** Review the section about casting in an inheritance hierarchy, and recall that an object behaves according to what it actually is, not what it is called.

**[Solution]**

```java
Read it.
Ship it.
Buy it.
Read it.
Box it.
Read it.
```



* **[R-2.13]** Consider the following inheritance of classes: 

    * Class `Goat` extends `Object` and adds an instance variable `tail` and methods `milk( )` and `jump( )`.
    * Class `Pig` extends `Object` and adds an instance variable `nose` and methods `eat(food)` and `wallow( )`.
    * Class `Horse` extends `Object` and adds instance variables`height` and `color`, and methods `run( )` and `jump( )`.
    * Class `Racer` extends `Horse` and adds a method `race( )`.
    * Class `Equestrian` extends `Horse` and adds instance variable `weight` and `isTrained`, and methods `trot( )` and `isTrained( )`.

    
    Let `d` be an object variable of type `Horse`. If `d` refers to an actual object of type `Equestrian`, can it be cast to the class `Racer`? Why or why not?
    

**[Hint]** Casting in an inheritance relationship can only move up or down the hierarchy.

**[Solution]** No, d is referring to an Equestrian object that is not also of type Racer. Casting in an inheritance relationship can only move up or down the hierarchy, not “sideways.”



## Implementation

* **[C-1.20]*** Write a Java method that 1) creates an integer array of 100 items which are randomly selected between 1 and 1000, and 2) determines if all the numbers are different from each other (that is, they are distinct).

**[Hint]** Use Random class to generate numbers. The simple solution just checks each number against every other one, but we will discuss better solutions later in the book. Make sure you don’t compare a number to itself.

**[Solution for Step 2]**

```java
public boolean distinct(int[ ] data) {
    for (int j=0; j < data.length − 1; j++) {
        for (int k=j+1; k < data.length; k++) {
            if (data[j] == data[k])
                return false;
        }
    }
    return true;
}
```



* **[C-1.22]** Write a short Java program that outputs all possible strings formed by using the characters 'c', 'a', 't', 'd', 'o', and 'g' exactly once.

**[Hint]** There are many solutions. If you know about recursion, the easiest solution uses this technique. Otherwise, consider using an array to hold solutions. If this still seems to hard, then consider using six nested loops (but avoid repeating characters and make sure you allow all string lengths).

**[Solution]** Here is a possible solution:

```java
public static void permute(ArrayList bag, ArrayList permutation) {
    // When the bag is empty, a full permutation exists
    if (bag.isEmpty( ) ) {
        System.out.println(permutation);
    } else {
        // For each element left in the bag
        for(int i = 0; i < bag.size( ); i++) {
            // Take the element out of the bag
            // and put it at the end of the permutation
            Object obj = bag.get(i);
            bag.remove(i);
            permutation.add(obj);
            // Permute the rest of the bag (recursively)
            permute(bag, permutation);
            // Take the element off the permutation
            // and put it back in the bag
            permutation.remove(permutation.size( ) − 1);
            bag.add(i, obj);
        }
    }
}

public static void main(String[ ] args) {
    ArrayList<Character> orig = new ArrayList<>( );
    char[ ] word = {'c', 'a', 't', 'd', 'o', 'g'};
    for (char c : word)
        orig.add(c);
    permute(orig, new ArrayList( ));
}
```



* **[C-2.28]** Write a set of Java classes that can simulate an Internet application in which one party, Alice, is periodically creating a set of packets that she wants to send to Bob. An Internet process is continually checking if Alice has any packets to send, and if so, it delivers them to Bob’s computer; Bob is periodically checking if his computer has a packet from Alice, and if so, he reads and deletes it.

**[Hint]** Use three different classes, for each of the actors, and provide methods that perform their various tasks, as well as a simulator engine that performs the periodic operations.



* **[P-2.35]** Write a Java program that inputs a list of words, separated by whitespace, and outputs how many times each word appears in the list. You need not worry about efficiency at this point, however, as this topic is something that will be addressed later in this book.

**[Hint]** You need some way of telling when you have seen the same word you have before. Feel free to just search through your array of words to do this here.