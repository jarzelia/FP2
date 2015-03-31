# Final Project Assignment 2: Explore One More! (FP2) 
DUE March 30, 2015 Monday (2015-03-30)


### My Library: Plot

The second library used is the Plot library, used for mathematical expressions and graphing.  To start, I put in a simple line of code.  This just draws y=x.

```
(plot (function (lambda (x) x) -2 2 #:label "y = x"))
```

Then, I added fiddled around with the labels a bit more and plotted multiple lines.  The next one explicitly passes boundaries to Dr.Racket, along with giving names and labels to the individual lines and a change of color.  The functions drawn are also explicitly bounded, since errors will be thrown if none is given, as there will be no way for the code to determine a proper default bounding box. 

```
(plot (list (axes)
            (function (lambda (x) (* x 3)) -3 3 #:label "y=3x")
            (function sqr -3 3 #:label "y=x^2" #:color 3)
            )
      #:x-min -3 #:x-max 3 #:y-min -3 #:y-max 9)
```

By adding a bit more, it looks like you could start to approximate calculus here.  There are labeled points of intersection, and the area between the two lines is drawn in.  However, what currently is here is all hard coded.  I have no doubt that this could be done using higher order procedures, except for the drawing of the points.  Unless the data returned was in a list format and the function knew how to parse the information.  Either way, if the two mathematical functions were passed in, one procedure could take care of all the drawing and plotting of what is between.

```
(plot (list (axes)
            (function (lambda (x) (* x 3)) -3 3 #:label "y=3x")
            (function sqr -3 3 #:label "y=x^2" #:color 3)
            (function-interval (lambda (x) (* 3 x)) (lambda (x) (* x x)) 0 3
                               #:color 2 #:line1-width 0 #:line2-width 0)
            (point-label (vector 0 0))
            (point-label (vector 3 9) #:anchor 'right)
            )
      #:x-min -3 #:x-max 3 #:y-min -3 #:y-max 10)
```

Finally, here is a bit of work with 3d rendering.  This is a lot more strict with the arguments it accepts.  It is just a little bit of work with 2 surfaces.  Still pretty interesting to see, and the possibilities of doing graphical calculus is definitely there.

```
(plot3d (list (surface3d (λ (x y) (+ (sqr x) y)) -2 2 -2 2)
              (surface3d (λ (x y) (+ (- (sqr x)) (- (sqr y)) 4)) -2 2 -2 2 #:color 4)))
```

[Here is a link to all of the screencaps.][pictures]

<!-- Links -->
 [pictures]:http://imgur.com/a/HXSf1
