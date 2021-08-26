# Solving a Rubik's Cube

This is definitely not the only way to solve a cube, but it's the way I learned.


## General Notes, Terminology, etc.

Saying that a side "is" a particular color refers to only the center dot on a side.
Referring to "the blue side", for instance, would refer to the side with the blue dot in
the middle.  I.e. - The blue side is the blue side even if ONLY the center dot is blue.

Which side is the TOP, FRONT, LEFT, RIGHT, BACK, or BOTTOM is entirely dependent on how
you are holding the cube at the time.  The assumption is always that you are looking at
the cube face-on, with FRONT facing you, BACK being the side opposite that, and LEFT,
RIGHT, TOP, and BOTTOM being fairly self-explanatory from there.

Key to the cube "diagrams" (if you'll excuse the exaggeration):
<dl>
    <dt>X</dt>
    <dd>(Any letter, that is.)  One specific color on the entire cube.  So for example an
        &quot;A&quot; would be a particular color, and would be that same color across
        sides in a particular diagram.  Unless otherwise noted, a specific letter probably
        won't refer to the same color from diagram to diagram.</dd>
    <dt>.</dt>
    <dd>Any color.  Basically, a placeholder to mark a spot whose color doesn't matter in
        the context of that diagram.</dd>
</dl>

The algorithms referred to in the steps are described below.


## Steps

1. Solve one face such that each of the edges is the same color as its respective face's
   center dot.

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   A A A  B B B  C C C  D D D  E E E  . . .
   A A A  . B .  . C .  . D .  . E .  . . .
   A A A  . . .  . . .  . . .  . . .  . . .
   ```

1. Move the middle side pieces to their correct spots.

   **TODO**

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   A A A  B B B  C C C  D D D  E E E  . . .
   A A A  B B B  C C C  D D D  E E E  . . .
   A A A  . . .  . . .  . . .  . . .  . . .
   ```

1. Turn the cube over such that the old TOP is now the BOTTOM.  Make a "plus" on the new
   TOP, using FRU-RUF.

   **TODO**

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   . A .  . . .  . . .  . . .  . . .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

1. Move the "plus"'s ends such that they're aligned with their correct sides, using RU2 or
   LU2.

   **TODO**

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   . A .  . B .  . C .  . D .  . E .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

1. Manipulate the corner pieces until there's at least one corner in its correct spot,
   using LURU2.

   **TODO**

   The cube should now look like this, but with the condition that at least one of the TOP
   corners' colors should be the same colors as all of its corresponding sides, even if
   they're not in the correct orientation.  Example: Let's say TOP is blue, RIGHT is
   white, and BACK is red.  If the corner piece adjacent to all three of those sides (in
   other words, the TOP-RIGHT-BACK corner) is the red+white+blue corner piece, the
   condition is fulfilled, regardless of whether the white face of the piece is on the
   RIGHT side of the cube at this point.

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   . A .  . B .  . C .  . D .  . E .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

1. Hold the cube such that corner piece that's in its correct spot is in the
   TOP-RIGHT-FRONT position.  Use LURU2 repeatedly from this position until the remaining
   corners are all in their correct places (color-wise) as well.  Orientation still
   doesn't matter at this point.  None, some, or even all of the corners may be correctly
   oriented.

   **TODO**

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   A A A  B B B  C C C  D D D  E E E  . F .
   A A A  B B B  C C C  D D D  E E E  F F F
   A A A  . B .  . C .  . D .  . E .  . F .
   ```

1. Use RU2+LU2 to rotate the corners into their final correct orientations.

   **TODO**

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   RIGHT  BACK   BOTTOM
   A A A  B B B  C C C  D D D  E E E  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   ```

1. Bask in the glow of your success.


## Algorithms

General Notes

* In the descriptions below, "U" stands for "Upper", which would be "TOP" in the diagrams.
  Using "U" just put a vowel in the acronyms, which made them somewhat pronouncable and
  helped them stick in my brain when I was learning them.  :)  YMMV
* CW  = clockwise
* CCW = counter-clockwise
* X  = Rotate side X 90' CW    (ex: R  == rotate the RIGHT side 90' CW)
* X' = Rotatate side X 90' CCW (ex: R' == rotate the RIGHT side 90' CCW)
* Individual pieces are designated by SIDE-EDGE-PLACE, so TOP-LEFT-MIDDLE is the piece
  located on the TOP side, on the LEFT edge of the side, in the MIDDLE position.
  * **TODO** - Think through this - make it more rigorously defined.

### FRU-RUF

Used repeatedly to form the "plus".

Creates this...

```
TOP
. A .
A A A
. A .
```


Short form: **FRUR'U'F'**

Long form:

1. Rotate FRONT 90' CW
1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CW
1. Rotate RIGHT 90' CCW
1. Rotate TOP 90' CCW
1. Rotate FRONT 90' CCW


### LURU2

Rotates TOP-FRONT-LEFT, TOP-BACK-LEFT, and TOP-BACK-RIGHT one place CW.

I.e. - It turns this...

```
TOP
Y . Z
. . .
X . .
```

...into this...

```
TOP
X . Y
. . .
Z . .
```

Where X, Y, and Z refer to the same colors between those two diagrams.

Short form: **LU'R'UL'U'RU**

Long form:

1. Rotate LEFT 90' CW
1. Rotate TOP 90' CCW
1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CCW
1. Rotate LEFT 90' CW
1. Rotate TOP 90' CW
1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CCW


### RU2

Moves TOP-LEFT-MIDDLE, TOP-BACK-MIDDLE, and TOP-RIGHT-MIDDLE one place CCW on the TOP
side.

I.e. - It turns this...

```
TOP
. Y .
X . Z
. . .
```

...into this...

```
TOP
. X .
Z . Y
. . .
```

Where X, Y, and Z refer to the same colors between those two diagrams.

Preserves orientation of the moving pieces (I.e. - the TOP side of each piece stays on the
TOP side).  Also preserves the positions/orientations of all pieces in the cube except for
those on the TOP side.  Other pieces on TOP are moved and/or rotated, but they don't
matter in the contexts in which this algorithm is used.

Short form: **RUUR'U'RU'R'**

Long form:

1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CW
1. Rotate TOP 90' CW
1. Rotate RIGHT 90' CCW
1. Rotate TOP 90' CCW
1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CCW
1. Rotate RIGHT 90' CCW


### LU2

Moves TOP-LEFT-MIDDLE, TOP-BACK-MIDDLE, and TOP-RIGHT-MIDDLE one place CW on the TOP side

I.e. - It turns this...

```
TOP
. Y .
X . Z
. . .
```

...into this...

```
TOP
. Z .
Y . X
. . .
```

Where X, Y, and Z refer to the same colors between those two diagrams.

Preserves orientation of the moving pieces (I.e. - the TOP side of each piece stays on the
TOP side).  Also preserves the positions/orientations of all pieces in the cube except for
those on the TOP side.  Other pieces on TOP are moved and/or rotated, but they don't
matter in the contexts in which this algorithm is used.

Short form: **L'U'U'LUL'UL**

Long form:

1. Rotate LEFT 90' CCW
1. Rotate TOP 90' CCW
1. Rotate TOP 90' CCW
1. Rotate LEFT 90' CW
1. Rotate TOP 90' CW
1. Rotate LEFT 90' CCW
1. Rotate TOP 90' CW
1. Rotate LEFT 90' CW


### RU2+LU2

Rotates TOP-RIGHT-BACK 90' CW in-place, and TOP-RIGHT-FRONT 90' CCW in-place

I.e. - It turns this...

```
TOP    FRONT  RIGHT  BACK
. . A  . . Y  Z . B  C . .
. . .  . . .  . . .  . . .
. . X  . . .  . . .  . . .
```

...into this...

```
TOP    FRONT  RIGHT  BACK
. . B  . . X  Y . C  A . .
. . .  . . .  . . .  . . .
. . Z  . . .  . . .  . . .

```

A, B, C, X, Y, and Z all refer to the same colors between those two diagrams.

Preserves EVERYTHING else on the whole cube except those two pieces.

Steps: Execute **RU2** and **LU2** consecutively (either order works).
