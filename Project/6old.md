# 6_old_

## A shape-drawing microworld in Java

Let's imagine learning to program using Java.

Idea: I want to draw a red circle on the screen! (We use a visual example because we assume that numerical or text-based programs executed at the command line or not as engaging as drawing things on the screen.)

Implementation:
1. Import things
2. Create a class
3. Create a main method
4. Create a buffered image
5. Get a graphics context from the buffered image
6. Set the paint component of the graphics context
7. Call the actual drawing method of the graphics context
8. Dispose of the graphics context

Already we see quite a gap between idea and implementation.

Evaluation:
1. Install Java
2. Set up classpath
3. Set up an editor
4. Save file with implementation in it
5. Compile implementation file
6. Execute implementation file

Only after carrying out all of these steps are we able to see the results of our idea. IDE's eliminate some of these steps, but most IDE's are not trivial to set up themselves. 

As we argued above, the tighter the feedback loop, the more engaging the experience, and the better an environment is for learning.

## An ideal shape-drawing microworld

So what would an ideal version of our circle-drawing example look like?

Idea: I want to draw a red circle on the screen! (Exactly the same as above).

Implementation: 
1. `Draw a red circle on the screen`.

Our implementation would be our idea unambigously specified for machine understanding. We would not have to specify anything unnecessary, only things regarding what we want to do:
1. Draw
2. a red circle
3. on the screen

Evaluation:
1. The editor in which we wrote our implementation would evaluate it, actually drawing a red circle to the screen.

If our idea-implementation-evaluation loop was this tight, we'd be able to use the results of our evaluation to quickly update our ideas, alter our implementation, and see what effect was produced when evaluating.

This would help us build up an *intuitive understanding* of how our ideas can affect this shape-drawing microworld, without needless overhead making our experience tedious.

## A shape-drawing microworld in Lisp

Idea: I want to draw a red circle on the screen! (Exactly the same as above).

Implementation:
(circle
  (position "50%" "50%")
  (radius 200)
  (fill "red"))

This corresponds to: "Draw a red circle at the location (50%, 50%) with a radius of 200 pixels." We need to do this as "on the screen" is too ambiguous - our machine needs to be told where to draw, and how big to make the circle.

Unlike the Java version, we don't have to import anything, create a class, or a main method. We don't have to create a BufferedImage, or execute methods of a (conceptually) abstract graphics context. Everything we do is relevant to the domain of drawing shapes on the screen.

Evaluation:
1. Go to http://draw.talkingtomachines.org
2. Enter the implementation in the editor
3. Press Command + Enter

![][image-1]

Unlike the Java version, we don't have to install and configure a runtime environment. We leverage the JavaScript runtime environment that is loaded every time a user navigates to a web page.

We don't have to set up an editor as one is provided. We don't have to create a build configuration as that is set up: pressing Command + Enter parses, compiles and executes the code in the editor for us.

# Does this improve on the Java version?

Let's say the circle we drew was too big. This is an update of our idea.

We change our implementation: 
(circle
  (position "50%" "50%")
  (radius 100)
  (fill "red"))
and then press Command + Enter. 

Our evaluated idea is immediately shown next to our implementation, so we can consider it and perhaps iterate further.

In the Java version, we would have to update our source code (which is not itself directly connected to our original idea) in our editor, compile our code, and then execute it, to see the results in a file that we have to use a suitable program to open.

The idea-implementation-evaluation loop takes longer to iterate. According to our theoretical framework, this makes the Java version worse.

## What else can we do with our Lisp microworld?

Concentric circles:
(for-each \[r (integers :from 800 :to 0 :step -20)\]
  (circle
(position "50%" "50%")
(radius r)
(stroke-width 3)
(stroke "black")
(fill (rand-nth colors))))

Here we used our original program as a subcomponent of a larger, more complex program...

## What problems are there with our Lisp microworld?

Vocabulary and syntax of a new language need to be explained: hand-holding.

## Why is being in the browser so important?

Accessibility etc.

---- 
* In the browser - accessing a programming environment has never been this easy.
* But still need hand-holding. A software tutorial could work, but human one-on-one tuition would be preferable.
* Tech difficulties -\> change domain


[image-1]:	/img/ttmachines.png