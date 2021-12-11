---
layout: post
title:  "MVC and Design Patterns"
date:   2021-12-10 16:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">

## Separation of Concerns

![img.png](/assets/mvc_designpatterns/img.png?style=centerme)
- Divide program into small sections that are completely seperate and no intertwined dependencies

## Common Program Design

- Typical interactive program
  - It has three parts
  - Some way of interacting with the program
  - Some data structures that model the problem the program solves
  - Some code that responds to the interaction and use the data structures to do some work
![img_1.png](/assets/mvc_designpatterns/img_1.png?style=centerme)

## Designing an Architecture

- MVC is an architecture not a design pattern
- Another architecture is client server where you have a server that process requests and provides resposnses to a
  client
- Another architecture is peer to peer

## Model/View/Controller

![img_3.png](/assets/mvc_designpatterns/img_3.png?style=centerme)
- MVC is a design pattern inside the observe observable pattern -Observer Observable doesn't have anything to do with
  the model
- Tic tac toe implementation should be able to switch from storing characters to booleans without having to change the
  model
- Controller is universal
- Model has nothing to do with the rules of the game

## What does MVC buy us

![img_4.png](/assets/mvc_designpatterns/img_4.png?style=centerme)
- Should be able to change the model without changing the controller or the view
- Should be able to change the view without changing the controller of the model

## Exception and MVC

![img_5.png](/assets/mvc_designpatterns/img_5.png?style=centerme)
- Exceptions allow us to seperate concerns and handle errors where we want to

## MVVM Model-View-ViewModel

![img_6.png](/assets/mvc_designpatterns/img_6.png?style=centerme)
- common design among single page applications
![img_7.png](/assets/mvc_designpatterns/img_7.png?style=centerme)
- instead of view calls controller->controller modifies model ->model updates view
  we use binded data between the model and view
![img_8.png](/assets/mvc_designpatterns/img_8.png?style=centerme)

## Architectural Patterns

![img_9.png](/assets/mvc_designpatterns/img_9.png?style=centerme)

## Design Patterns

![img_11.png](/assets/mvc_designpatterns/img_11.png?style=centerme)
- Singleton pattern is a design pattern but some people say it's an antipattern
- Antipattern - common solution that is bad

## Singleton Design Pattern

![img_12.png](/assets/mvc_designpatterns/img_12.png?style=centerme)
- The idea is that we create a class with a private constructor and a field that is private and static for the
  single instance of the class
- Then we have a public get instance method that either creates the single instance or it returns the static
  instance if it already exists
  **- Java uses the singleton design pattern for the Runtime object**
![img_13.png](/assets/mvc_designpatterns/img_13.png?style=centerme)
- Runtime is a singleton because Runtime is represent the physical hardware/operating system the code is running on
- **code smell - more then one dot on a method in Java, because sometimes you will get different instances of the
  object**

![img_14.png](/assets/mvc_designpatterns/img_14.png?style=centerme)
- bad to use in practice
