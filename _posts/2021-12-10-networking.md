---
layout: post
title:  "Networking"
date:   2021-12-10 14:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">


## What is Networking

- Networking is having programs on seperate computers interact with one another
- Client - Server
  - server = computer + application that is in charge
- Peer to Peer
  - both computers are the same level
  - some things more difficult if no one is in charge
![img.png](/assets/images/img.png?style=centerme)

## How Does Networking Work?

- Computers are connected to each other through links called **sockets**
  - **socket = potential or actual connection to another**
- A network stream is created by connecting a socket on one computer to a socket on another
  - each has an input and output stream
- Applications communicate by rteading and writing data through stream to each other
- We primarly care about the Application layer in netwworking
- our output becomes the other computers input and our input will be the other computers output
![img_1.png](/assets/images/img_1.png?style=centerme)

## Sockets

- A socket is connection n one computer for sending data back and forth
- Sockets are created by the process on each computer
  - A process is a running program
    - A program is a collection of code + data with it's own state
- The sockets then establish a connection to each other
  - The server sets up a ServerSocket object to recieive connections using a specfic port number
    - server is special process that is in charge
  - The Client sets up a Socket object to request a connection with the server
    - client is one of many processes that wish to talk to the server
- Example: Misurda is the server for office hours, students that attended office hours are client
![img_2.png](/assets/images/img_2.png?style=centerme) 

## Client-Server Networking

- Advantages
  - Easier to implement
  - Less coordination involved
  - Easier to maintain control of users
- Disadvantage
  - Relies on one main server for entire operation

## Peer-to-Peer Networking

- Advantages
  - No main server
  - Easier for clients to enter and leave
  - Easier for spreading updates
- Disadvantages
  - less control over users
  - harder to coordinate
  - more difficult to implement code
![img_3.png](/assets/images/img_3.png?style=centerme) 

## We Use LocalHost

- You won't need to rent a server
  - Every computer can be a server
  - Your machine has a know IP address: localhost or 127.0.0.1
- local server - client implementation
  - we launch two instances of the same program one instance is the client one instance is the server
  - we run the server code first so their is a server to connect to
    - this process is blocking on the server instance of the program
  - then we run the client code to connect to the server
    - we write an object to the server
    - the server will write objects back to the client
- **IP adresses are adresses for computers, ports are adresses for processes on that computer**
  - Example: Apartment complex has an adress = IP adress, Each apartment has an apartment number = port
- Protocol
  - If server listening -> client is talking
  - If client listening -> server is talking
  - If both listening nothing happens
  - If both talking then we cannot recieve either message
- HTTP
  - Client talks first -> "Get index.html"
  - Server listens and gives the webpage
![img_4.png](/assets/images/img_4.png?style=centerme) 

## Classes ServerSocket and Socket

- Found in the java.net framework
- ServerSocket
  - accept new incoming connections from clients
- Socket
  - requests a connection to the server
![img_5.png](/assets/images/img_5.png?style=centerme) 

## Sockets in Jva: One-Way Communication

- Typical web server
![img_6.png](/assets/images/img_6.png?style=centerme) 

## General Networking Flow

![img_7.png](/assets/images/img_7.png?style=centerme) 

## Server - java.net.ServerSocket

- takes port as parameter to constructor
- accept()
  - waits for incoming connection, establishes the new connection and returns a regular socket for that
    connection
  - is a blocking process until a client connection is recieved
- we can have multiple clients connect to the same server socket
![img_8.png](/assets/images/img_8.png?style=centerme)

## Client - java.net.Socket

- takes the String host and int port as the constructor and connects to server at the provided ip and port
- inputStream and outputStream allow us to send serialized java data with decorators between the two sockets
![img_9.png](/assets/images/img_9.png?style=centerme)

## Reserved Ports

- Common example is port 80 is used for HTTP
![img_10.png](/assets/images/img_10.png?style=centerme) 

## Server Code Example

- Import details
  - ServerSocket is a potential connection
  - server.accept() - is blocking until client connects, returns a regular Server object so we can send and recieve data
  - create input and output stream to send and recieve data that are linked to the inverse of the client our input
    is client's output our output is client's input
![img_11.png](/assets/images/img_11.png?style=centerme) 

## Client Code

- Server() constructor takes an ip adress and a port that matches our server
- The server has to be active or we get an exception
- Create the input and output streams inversely connected to the server our input is server output server input is
  client output
![img_12.png](/assets/images/img_12.png?style=centerme) 

## Live Demo

- Should create a message class to serialize the communication
- When client calls outputstream.write -> it is sent to the servers inputStream.read, when client calls
  inputstream.read it reads the data from the server outputstream
- Currently we cannot have both the server and client listening or writing we need to process each write with a read
  before we do another write
-
