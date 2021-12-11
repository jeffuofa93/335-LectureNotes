---
layout: post
title:  "IO and Serialization"
date:   2021-12-10 16:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">

## Java I/O Framework Design Philosophy

![img.png](/assets/io_serialization/img.png?style-centerme)
- because the variation between operating systems their is a lot that goes into being able to do IO on different OS's
- I/O

## Java IO: IOEXception

![img_1.png](/assets/io_serialization/img_1.png?style=centerme)
- base exception for all exceptions thrown by the io package
- most IO exceptions should be checked

## File and Directory Operations

- File is an arbitrary ordered sequence of bytes
- Directories and Files are a compositive pattern, a directory is a file and can contain files like in javaFX layout
![img_2.png](/assets/io_serialization/img_2.png?style=centerme)
- MetaData is information about a file that is not contained inside that files contents
  - Example: files don't contain a line that says filename = notes.txt
  - Their is metadata that your OS stores that contains information about the file seperate from the files contents
- Recursive directory listing example
  - DFS on each file, if it's a directory recursively call the method until you reach a non directory file

## Java IO Streams

![img_3.png](/assets/io_serialization/img_3.png?style=centerme)
- Stream is an ordered sequence of bytes-8bits, of indeterminadte length
  - sequence can be fixed size like a file or continous like mouse input from a user
- Streams can be used to carry data from one part of a Java program to another
  - we have byte streams and character streams in java
- Streams of note
  - System.in - keyboard input
  - System.out - console
  - System.err - console, different to be explicit when outputting an error, also executes immediatly opposed to
    sys.out

## Character and Byte Streams

- Byte steams are used for compact and efficient I/O of primitive data as well as object and array, in machine readable
  form
- Character Streams are used for I/O from text files and human readable output. They use 16-bit unicode characters
  - The classes for chacterer streams are called Readers and WRiters
![img_4.png](/assets/io_serialization/img_4.png?style=centerme)
- **Character streams do the cannocicalization of line endings when they are read in to make them all the same and
  converts them when they go out to the correct format for the given operating system**

## Text/Character-Oriented Streams

![img_5.png](/assets/io_serialization/img_5.png?style=centerme)
- How to represent text in bytes?
- We map each letter to an integer value
- We need a standard agreement to share between all systems
- One Solutio ASCII
![img_6.png](/assets/io_serialization/img_6.png?style=centerme)

## ASCII Control Codes

![img_7.png](/assets/io_serialization/img_7.png?style=centerme)
- characters don't just represent letters they can represent actions like newline adn tab
![img_8.png](/assets/io_serialization/img_8.png?style=centerme)

## Line Ending Conversion

![img_9.png](/assets/io_serialization/img_9.png?style=centerme)
- We take the CR & LF or just the CR or just the LF and **cannocincalize** all of them to just be LF. This is why the
  orignal file size would be shrunk on windows
- System.out.println does the reverse it takes the LF and converts it to the correct CR or LF or CRLF for the current
  operating system

## Unicode

- Unicode has 1 million possible characters
- ASCII 1 char = 1 byte
- Unicode fixed length - 1 char = 4 bytes
- UTF -8 and UTF-16 variable length encodings

## Reading bytes with FileInputStream

![img_10.png](/assets/io_serialization/img_10.png?style=centerme)
- FileIntputStream is a byte oriented stream
- reads 1 byte and returns an int if it returns -1 it reached the EOF
![img_11.png](/assets/io_serialization/img_11.png?style=centerme)
- java FileInputStream returns an integer to be able to use -1 as a sentinal value to tell when it hints an EOF
- this is in bound

## Java I/O Primitives: Beyond Types

- **Deserialization - taking the byte input and reassembly the data **
  - exanoke taking bytes and turning them into bits

## Wrapper Class

- allows us to take an exisisting object and adding it to a new class instance the retains all the functionality of
  the original class plus any additional functionality added in the wrapper class
![img_12.png](/assets/io_serialization/img_12.png?style=centerme)
- example dataInStream.readFloat(), calls the filestrean.read 4 times and deserializes it into a float

## The Decorator Pattern

- same as the wrapper described above
- **The decorator pattern uses the has A relationship to add additional functionality to a given class**
- **This is preffered over inhertinance because the wrapped is a data input stream and the inner class just has to
  be a stream so it could work for a network input stream or any input stream**
- **If we used inheritance then we would need a dataFileInput subclass of FileInputStream and a dataNetworkInput
  subclass of network streams**
- **The amount of subclasses would become unwiedly we would be type restrictied to the original stream class**
- **A decorator can be both a decorator and a concreteComponent so we can implement decorators on top of other
  decorators to provide additional functionality but in this case the concreteComponent is replaced by the decorator
  that is below the top decorator**
![img_13.png](/assets/io_serialization/img_13.png?style=centerme)

## UML for the Decorator Patter

- Ex: the dataStream decorator
- We have the abstract component inputStream that must implement a read method
- We have a concreate component, FileInputStream or NetworkInputStream that implements the read method
- We have an abstract decorator class that is required to contain an implemented inputStream and provide access to
  all of its methods
- Then we have concrete decorators that augment the inputStream to provide implementations of extended functionality
  such as readFloat the calls the inputStream read method 4 times and returns the result
![img_14.png](/assets/io_serialization/img_14.png?style=centerme)
![img_16.png](/assets/io_serialization/img_16.png?style=centerme)
- Important not that because the DataInputStream provides all the functionality of a regular inputStream we can then
  forward that dataInputStream to another wrapper as a regular input stream

## Example Java's Input Character STreams

![img_17.png](/assets/io_serialization/img_17.png?style=centerme)
![img_18.png](/assets/io_serialization/img_18.png?style=centerme)
![img_19.png](/assets/io_serialization/img_19.png?style=centerme)

## Java I/O: Closeable

![img_20.png](/assets/io_serialization/img_20.png?style=centerme)

## Java I/O" Buffering and Flushing

- Buffer prints to screen when it becomes full
![img_21.png](/assets/io_serialization/img_21.png?style=centerme)

## Redirecting In, Out and Err

- We can redirect the output of our java programs to other places like files
![img_22.png](/assets/io_serialization/img_22.png?style=centerme)

## Useful System Properties

![img_23.png](/assets/io_serialization/img_23.png?style=centerme)

# Serialization

- **Big Idea we can instead of taking a java object and parsing it into a string and writing it to a file we can
  write and entire object including all of it's references abd convert it into bytes**
- **This is call serialization**
- **The process of reconstructing the object from the bytes is called deserialization**
- **Java provides easy ways to do this with another set of wrappers around streams**
![img_24.png](/assets/io_serialization/img_24.png?style=centerme)

## java.io.Serialiable

- To be able to be serializable you need to implement the javaa.io.Serializable interface that allows your class to be
  serialized
- Must declare static final long serialVersionUID = id;
![img_25.png](/assets/io_serialization/img_25.png?style=centerme)

## Object streams

- ObjectOutputStream is the wrapper class that allows you to write a serializable class
- ObjectInputStream is the wrapper class that allows to read a serializable class
  - readObject() can throw an io exception if either the serializable object can't be found which mainly contains
    the fields OR if the .class file for the written class cannot be found
![img_26.png](/assets/io_serialization/img_26.png?style=centerme)

## Serializable Marker Class

![img_27.png](/assets/io_serialization/img_27.png?style=centerme)

## Sending a Graph of Objects

- What happens if a field is a reference to another instance
- **IMPORTANT all references from the root class to other classes must also be serializable**

## Serialization pitfalls: transient modifier

- **transient modifier for fields are not written out during serialization**
- **fields marked transient are skipped**
- Reason to skip would be if you have a password and you don't want it written
- Another example would be a random seed for a game
![img_28.png](/assets/io_serialization/img_28.png?style=centerme)

- Also we can define special reaObject and writeObject methods to for example prompt the user for input to fill
  missing data from a serialized class that has fields marked as transient
- We can also change the object fields for things that are not transient but this is the main use case
![img_29.png](/assets/io_serialization/img_29.png?style=centerme)

- If you write an object to a file and then you change the object and want to write it again, writing the object
  again to the same file will create to instances of the object
- What you probably want to do is deleted the first object and then write the modified object

## Stringify vs Serialization

- stringification has the advantage of not being dependent on the specific programming language and it human readable
- Ex: using JSON in javascript with any backend
- serialization advantages is that it's most more efficent that writing data to text
-
