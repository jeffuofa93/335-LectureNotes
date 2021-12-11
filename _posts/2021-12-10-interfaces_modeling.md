---
layout: post
title:  "Interfaces and Modeling"
date:   2021-12-10 16:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">

## IsA vs HasA
- Inhertiance is isA composition is hasA. 

### Should it be IsA or HasA
- Given a radio, Write a car
  - car hasA radio
- Given a computer, write a laptop 
  - laptop isA computer
- Given a player write a team 
  - team hasA player
- Given a abstract set write a sorted set 
  - sortedSet isA abstractSet
- Given an ArrayList write a Queue
  - queue isA arraylist?
- Given a doctor wrrite a lawyer
  - interface? 
#### SPECIAL
- Given a file write a folder
  - folder isA file 
  - folder hasA file (many)
  - unix system implementation 
- Given a student write a UGTA
  - UGTA isA student 

### Java's Inheritance Model
- Single Inheritance
  - every class can only have one parent class
  - This is to avoid the diamond problem where you inheret the same method from two parent classes and it's not 
  clear what implementation should be user
- Classes with different parents can still be grouped together conceptually using interfaces
  - ex: Collections have many different class heiracharies but are forced to have some common behavior

### OVerriding Methods 
- Overriding is the practice of writing a method in a subclass with the same partial signature as a method in the 
superclass it extends from 
- Since Object has a toString() method every time we write one we are actually overriding 
![img.png](/assets/interfaces_modeling/img.png?style=centerme)
- method needs the same name and param list in the subclass
- Special Notes
  - If you override the equals method you also need to update the hash method or vice versa

### Using super
- Many times when overriding methods or constructors you will want to reuse code from the same method in the superclass 
you extended. This can be done by using the keyword super
![img_1.png](/assets/interfaces_modeling/img_1.png?style=centerme)

### Overide Decorator 
![img_2.png](/assets/interfaces_modeling/img_2.png?style=centerme)
- if you have a typo in the method signature the override decorator would let the compiler catch that and say hey 
this is an overriden method but it doesn't override anything 

### Annotations
- form of metadata
  - data that describes data
  - provides information about a program that is not part of the program itself
- Annotations have no direct effect on the operation of the code they annotate
- Usecases
  - Information for the compiler 
    - mismatched method signature example
  - Compile-time and deployment-time processing
    - tools can use annotations to generate code like XML files
  - Runtime processing 
    - Some annotations can be examined at runtime

### Java Interfaces
- interface is just a list of methods without code 
- each implementing class has a CanDo relationship with that interface
  - That class must provide an implementation of each of the interfaces methods

### Declaring an interface
![img_3.png](/assets/interfaces_modeling/img_3.png?style=centerme)
- default implementation is somewhat of a hack that allows interfaces to be updated without breaking all 
implementations of that interface

### Implement an interface UML
![img_4.png](/assets/interfaces_modeling/img_4.png?style=centerme)

### Polymorphism and Casting
- Since a Student isA person, it can do everything a person can
![img_5.png](/assets/interfaces_modeling/img_5.png?style=centerme)
- Since this is an upcast the cast doesnt need to be explicit 

### Static vs Dynamic
- Static is a term that means "at compile time" or "before the program executes"
- Dynamic is a term that means "at run time" or "while the program is running"
- Java is a statically typed language that use dynamic dispathc

### Statically-Typed
- The compiler checks type compatability 
- Checks type assignment and method calling 
- Upcasting student to person makes it not compile if you try to call getGpa() on a person even though the code 
would work at runtime 

### Dynamic Dispath 
- What about our overridden methods?
![img_6.png](/assets/interfaces_modeling/img_6.png?style=centerme)
- ovverriden methods are called by the runtime type which keeps overrriden methods intact 

### Polymorphism and Casting 
![img_7.png](/assets/interfaces_modeling/img_7.png?style=centerme)
- This is changed in java 16 if we check instanceof inside the object is automatically casted inside the if block 

### Abstract Classes
- meant to be super class that are extended 
- provide code methods you want all classes to have 
- protype methods you want all subclasses to implement abstract methods 
- you  cannot instanstiate abstract classes 

### AC's and Interfaces
- Most implement all of the methdos of an interface or the class must be declared as an abstract class 
![img_8.png](/assets/interfaces_modeling/img_8.png?style=centerme)

### UML Summary
![img_9.png](/assets/interfaces_modeling/img_9.png?style=centerme)


