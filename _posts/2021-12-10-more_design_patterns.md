---
layout: post
title:  "More Design Patterns"
date:   2021-12-10 18:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">

## GoF Design Patterns

![img.png](/assets/more_designpatterns/img.png?style=centerme)

## Design Pattern Relationships

![img_1.png](/assets/more_designpatterns/img_1.png?style=centerme)

## The Factory Method Pattern

- Define the interface for creating an object while retaining control over which class to instantiate
- Also know as Virtual Constructor
![img_2.png](/assets/more_designpatterns/img_2.png?style=centerme)

## UML for the Factory Method Pattern

![img_3.png](/assets/more_designpatterns/img_3.png?style=centerme)

## Exmaple: Phone Calls

- we create a factory method that is called when trying to make a phone call
- The method returns a subclass of Call but abstracts away which subclass is returned
- We can have as many subclasses we want and use the data paased to the factory method to determine which subclass to
  return
![img_4.png](/assets/more_designpatterns/img_4.png?style=centerme)

## Phone Calls with Factory Method

![img_5.png](/assets/more_designpatterns/img_5.png?style=centerme)
![img_6.png](/assets/more_designpatterns/img_6.png?style=centerme)
![img_7.png](/assets/more_designpatterns/img_7.png?style=centerme)
- The logic behind what Call subclass is returned is encapsulated in the factory method
- The subclasses provided different implementations of the abstract talk() method
![img_8.png](/assets/more_designpatterns/img_8.png?style=centerme)

## Non-Factory Method

- Not all methods that return an object are examples of the Factory Method Pattern
- Factory Pattern Requirements
  - Create an object
  - Return an abstract class or interface
  - Implemented by concrete classes of an abstract class or interface
- toString()
  - Not a Factory Method because it does not return an abstract class
- List<E> Arrays.asList()
  - Very similar to the Factory Method Pattern 
  - Not a factory because the factory method itself is not abstract
![img_9.png](/assets/more_designpatterns/img_9.png?style=centerme)

## The Abstract Factory Pattern

- Create an abstract factory that creates a concrete factory that returns a concrete subclass instance
![img_10.png](/assets/more_designpatterns/img_10.png?style=centerme) 
![img_11.png](/assets/more_designpatterns/img_11.png?style=centerme)

## Abstract Factory Light and Dark Theme Example

- The idea here is say we have two different theme factories for our UI components.
- We create an AbsractFactory that has a concreteFacotryofFactories that returns either our light theme factory or 
  our dark theme factory depending on the time of day passed to our concreteFactortyOfFactories constructor 
- Then when we call get button on our concrete light or dark theme factory it returns the correct button for our 
  factory 
- We could also have get textbox and methods for any UI components connected to our factory


## The Prototype Pattern

![img_12.png](/assets/more_designpatterns/img_12.png?style=centerme)

## Cloning in Java

- when you call clone on an instance is returns an enteriely new instance of the object with the same state
- To be able to call clone on your class you need to implement the clonable interface
  - No methods required for cloneable interface just need to add it to the class

## Shallow versus Deep Copies

![img_13.png](/assets/more_designpatterns/img_13.png?style=centerme)
- Shallow copy exmaple: String a points to different String object then String b but the underlying characters 
  referenced are the same 
![img_14.png](/assets/more_designpatterns/img_14.png?style=centerme)
- Deep copy example: String a points to different String object then String b and the entirty of all the references 
  inside the fields are copied to a different location 
![img_15.png](/assets/more_designpatterns/img_15.png?style=centerme)
![img_16.png](/assets/more_designpatterns/img_16.png?style=centerme)

## Details of Overriding Clone()

![img_17.png](/assets/more_designpatterns/img_17.png?style=centerme)

## Summary of the Prototype Pattern

- Used when isntances differ only in properites not in behavior
- The cloned object copies the state of the original object
- That is why this prototype pattern is important in java we can create a copy of any object with the clone 
  - Also we can implement an override of clone ourselves the creates a deep copy
  - For a shallow copy we just have to implement the method less clonable interface