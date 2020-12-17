# CS61B Week 01

## 1.1 Intro,basic Java

### Introduction

**What is 61B about?**
Algorithms and data structures.


### First Java Program

#### Hello World

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

* All codes must be in a class.
* Curly braces and semi-colons.
* Variables have **declared** types and must be declared before use.
* Functions must have a **return type** or declared as **void** function.
* The compiler ensures type consistency.

#### Compilation

 `javac` and `java`.

```
$ javac HelloWorld.java # compiler
$ java HelloWorld # run
Hello World!
```

#### Defining Functions

Since all Java code is part of a class, we must define functions(method) so that they belong to some class. 

Eg: A function that could compare two integers and return the larger one.

```java
public class LargerDemo {
    public static int larger(int x, int y) {
        if (x > y) {
            return x;
        }
        return y;
    }

    public static void main(String[] args) {
        System.out.println(larger(8, 10));
    }
}
```

#### Code Style

* Comments (use `//` for line comments and  `/*` and `*/` for block comments)
* Descriptive naming (variables, functions, classes)
* We could use [Javadoc](https://en.wikipedia.org/wiki/Javadoc) to automatically generate documents.

## 1.2 Defining and Using Classes

### Defining Classes

* Must define a main method.

```java
public class Dog {
    public static void makeNoise() {
        System.out.println("Bark!");
    }
}
```

The code above can't be run directly because there's no main method.

```java
public class DogLauncher {
    public static void main(String[] args) {
        Dog.makeNoise();
    }
}
```

However, the method could be called from another class. 

```
$ java DogLauncher
Bark!
```

### Object Instantiation

* Classes can contain methods, data... (eg. the `size` of each dog.)
* Classes can be instantiated as objects. For example, create a single Dog class, and then create instances of this Dog.

```java
public class Dog {
    // Instance variable
    public int weightInPounds; 

    // Constructor
    public Dog(int startingWeight) { 
        weightInPounds = startingWeight;
    }

    // Non-static method (Instance method)
    public void makeNoise() {
        if (weightInPounds < 10) {
            System.out.println("yipyipyip!");
        } else if (weightInPounds < 30) {
            System.out.println("bark. bark.");
        } else {
            System.out.println("woof!");
        }
    }
}
```

```java 
public class DogLauncher {
    public static void main(String[] args) {
        Dog smallDog;          // Declaration
        new Dog(20);           // Instantiation
        smallDog = new Dog(5); // Instantiation and Assignment
        Dog hugeDog = new Dog(150); // Declaration. Instantiation, and Assignment
        smallDog.makeNoise();  // Invocaton
        hugeDog.makeNoise();   // The dot notation 
    }
}
```

### Array of Objects

To create an array of objects:
* First use `new` to create the array.
* Then use `new` again to put object that you want in the array.

```java
Dog[] dogs = new Dog[2];
dogs[0] = new Dog(8);
dogs[1] = new Dog(20);
dogs[0].makeNoise();
```

