---
layout: post
title:  "JavaFX Animation"
date:   2021-12-10 16:51:20 -0700
categories: jekyll update
---

<link rel="stylesheet" href="/assets/style.css">

## Animation

- JavaFx animation manipulate the value of one or more node properties at regular intervals
- Two basic ways to create animations
  - JavaFX Transition class
  - JavaFX TimeLine -> what we used in our project, custom canvas-based
- ![img.png](/assets/javafx_animation/img.png?style=centerme) \

## One Way: Use Transition Class

- create transition, then we can set the duration, the node to move, movement in x or y direction number of times to
  perform the given movement, autoreverse T or F determines if the node goes back to its original position in the
  given time
- ![img_1.png](/assets/javafx_animation/img_1.png?style=centerme)\

## PathTranslation Transition Class

- Path translation
  - we create a path object instance
  - we set a path in the grid by pixels we want the node to travel
    - moveTo - jumps without drawing
    - LineTo - draws the path from previous position
  - Then we create a pathTransition instance
  - set duration
  - setNode
  - setPath - to the path declared above
- ![img_2.png](/assets/javafx_animation/img_2.png?style=centerme) \

## TimeLine

- Timeline provides the capability to update the property values along the progression of time
- TimeLine needs to know two things
  - How often it needs to update the given properties of an object
  - Which properties to actually update
- This is done by each step in the timeline being a KeyFrame instance
- ![img_3.png](/assets/javafx_animation/img_3.png?style=centerme) \

## Using TimeLine

- timeLine object is passed a keyFrame with a duration, and an animationHandler
- The Timeline is going to add the keyframe events with the given handler to the javaFx event queu at the given
  duration increments
- setCycleCount - tells the timeline how many times we want this event to be added
- ![img_4.png](/assets/javafx_animation/img_4.png?style=centerme) \

## Animation Handler Example

- can also just handle with a lambda
- ![img_5.png](/assets/javafx_animation/img_5.png?style=centerme) \

## Example Timeline for the Competitive Timer in Chess

![img_6.png](/assets/javafx_animation/img_6.png?style=centerme) \

## Sprites

- **Sprite - is an image that is part of a larger graphics scene**
- **Sprite Sheet - allows us to combine multiple frames of an animation into a single image**
- ![img_8.png](/assets/javafx_animation/img_8.png?style=centerme) \

## ImageView.viewPort

- Gives us a way to crop an image
- We can create a large rectangle of all the images in our sprite sheet then
  inside a timeline we could crop each image to only show the specific image we want at that frame

## Sprites on a Canvas

- Draws the specific section of the image from the source rectangle to the specific position on the canvas
- ![img_9.png](/assets/javafx_animation/img_9.png?style=centerme) \

## Summary

- timeline is a way to add events to event queue in the future the events cannot be blocking or it will stop the
  processing of the event queue
- ![img_10.png](/assets/javafx_animation/img_10.png?style=centerme) \
