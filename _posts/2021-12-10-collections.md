---
layout: post
title:  "Collections"
date:   2021-12-10 16:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">

## The java.util Framework

- This framework is used to solve a common problems with the storage and retrieval of data
  - maintain order
  - quickly access data
  - handle any type of data
  - reduce the need to rewrite code

## Framework

- A framework is a design and implementation artifact
- It represents a specific domain and is
  - reusable
  - built of abstrac classes
  - implemented with concrete classes
- Good frameworks have
  - Reusable implementations
  - Well-defined boundaries in how it intercacts with cliets
  - An implementation that is hidden from the outside

## Java Collections

- Java's Collection Framework is a unified architecture for representing data

## ADT''s

- ADT's is a specification of the behavior of a type
  - Specifies method names to add, remove, find
  - Specifies if elements are unique, ...
- What Java construct nicely specifies ADTs
  - Interfaces

## Example Set ADT

![img_10.png](/assets/collections/img_10.png?style=centerme)

## Java Generics

- We want to be able to hold a collection of anything
- Our collections hold Objects

## Object Based Collections

- This is fine until we want to either
  - Get an element from a collection:

```java
Person p = collection.get(0) // error
Person p = (Person)collection.get(0) // have to have an explicit type
```

- Use static typing to ensure that we aren't adding elements the don't belong
  ![img_11.png](/assets/collections/img_11.png?style=centerme)
- If the type of the collection is object we can add anything to it

## What About Primitive Types

- All classes extend Object, but primitive types do not
- We have wrapper Objects that hold these to use in this case
- The java compiler will help us and do this automatically

## Auto-boxing

- We can do

```java
Object b = 3;
```

- Because the compuler rewrites our code to auto-box 3 into the appropriate java.lang.Integer class:

```java
Object b = new Integer(3);
```

- In some circumstances the compiler can unbox things

## Templates

- We can insert type info to get the compiler to verify that our collection is holding the proper things and also
  avoid having the

## Using Templates

- Older Style
  ![img_12.png](/assets/collections/img_12.png?style=centerme)
- Current Style
  ![img_13.png](/assets/collections/img_13.png?style=centerme)

## Type Erasure

- The inclusion of templated generics in Java happened in Java 5 well after Java already existed
- Java stole the template syntax from C++ which uses the same concept but implements it differently
  - In C++ if you create two instances of a templated class with different types it creates two different objects
    each with the actual type replacing the generic type
    ![img_14.png](/assets/collections/img_14.png?style=centerme)
- In java all the generic typing is erased as runtime and the generic array just becomes an array of objects

- Java doesn't create different classes instances based upon the type instead it uses a concept of type erasure

  - Type erasure means that the parameterized type only exists at compile time but is lost at runtime
    ![img_15.png](/assets/collections/img_15.png?style=centerme)

- What did the compiler do
  - In java generics are implemented by finding a type that can represent all things that T is allowed to be
- If T is unbounded T is pleaced by the compiler with Object
- Bounded tpes allow you to limit what a template accepts using the inheritance hierarchy
  - E extends Person says to only allow types that are a sublcass of Person
  - In this case the type isnt erased to Object but rather to Person

## Collection Interface

![img_16.png](/assets/collections/img_16.png?style=centerme)

- collection is an interface that extends another interface
- every collection in java has the collection interface method

## WildCard

![img_17.png](/assets/collections/img_17.png?style=centerme)

- ? is anytype
- ? extends E means any type that extends E

## List ADT

![img_18.png](/assets/collections/img_18.png?style=centerme)

- List is a more specfic interface off a collection
- Lists are collection and then some, Lists add a bunch of methods dealing with indexes
  ![img_19.png](/assets/collections/img_19.png?style=centerme)
- An array list is a concrete class that implements List, Collection and iterable interface
  ![img_20.png](/assets/collections/img_20.png?style=centerme)
- List has both an interface and an abstract class with some implementation

## Iterators

![img_21.png](/assets/collections/img_21.png?style=centerme)

- Iterator object provides the ability to walk over a collection. Doesn't matter if it's a linked list or an array
  list hides the implementation and just returns the next item
- Enhanced for loop is syntax sugar for iterator call and next
  ![img_23.png](/assets/collections/img_23.png?style=centerme)
  ![img_24.png](/assets/collections/img_24.png?style=centerme)
- Three loops indexed loop, verbose iterator and enhanced for loop which is syntax suger over verbose iterator
  implementation
  ![img_25.png](/assets/collections/img_25.png?style=centerme)
- Iterators are a design pattern to visit each element in a collection once
- Hashtable vs linked list vs tree vs array are different implementations but the iterator is the solution
  ![img_26.png](/assets/collections/img_26.png?style=centerme)
  ![img_29.png](/assets/collections/img_29.png?style=centerme)
  ![img_30.png](/assets/collections/img_30.png?style=centerme)
  ![img_31.png](/assets/collections/img_31.png?style=centerme)
  ![img_33.png](/assets/collections/img_33.png?style=centerme)
- ![img_34.png](/assets/collections/img_34.png?style=centerme)
- Ireterable says this method has an iterator
- Iterator returns the iterator object for that implementation

## Polymorphic Algorithms

- ![img_35.png](/assets/collections/img_35.png?style=centerme)
- if we can iterate and get and set elements then any algorithm can be applied to the list

## Entry Set with Array Map

- duck typed set. If we gurantee that we can only one of each key then
  the set is just the ability to iterator over the array of elements

## AbstractCollection

![img_36.png](/assets/collections/img_36.png?style=centerme)
![img_37.png](/assets/collections/img_37.png?style=centerme)

- Most of the collection implementations can be provided by the abstract
  class because we provide iterable and other methods
- Most java classes implement their own implementation for efficiently
  ![img_38.png](/assets/collections/img_38.png?style=centerme)
- Abstract map has a concrete implementation of get because of the iterator

## Template Method Pattern

![img_39.png](/assets/collections/img_39.png?style=centerme)

- Concrete subclasses need to provide concrete implementations of the variant behavior
- Abstract Class provides invariantBehavior that always work if the variant behavior has implementation
  ![img_40.png](/assets/collections/img_40.png?style=centerme)

## Floating point assertEquals

![img_41.png](/assets/collections/img_41.png?style=centerme)
