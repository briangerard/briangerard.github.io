# Solving a Rubik's Cube

This is definitely not the only way to solve a cube, but it is the way I learned (and so
far the only way I know).

The process is basically this:

1. Solve one side, making sure to align its edges with the center dots on its adjacent
   sides.
1. Move the middle row pieces into their positions, so now the top two rows of the cube
   are solved.
1. Make a "plus" sign on the bottom side of the correct color.
1. Align the "plus" sign's edge pieces with the correct adjacent sides (e.g. - so the blue
   edge piece is on the blue side, say).
1. Move the bottom side's corner pieces to their correct positions (but likely not yet
   oriented correctly).
1. Rotate the bottom side's corner pieces correctly.

So it's progressively solving it from one side to the opposite side, in other words.  Of
course, once you get into the details there are a few more steps involved. `;)`


## General Notes, Terminology, etc.

The algorithms referred to in the Steps section are described below in the Algorithms
section.

Saying that a side "is" a particular color refers to only the center dot on a side.
Referring to "the blue side", for instance, would refer to the side with the blue dot in
the middle.  I.e. - The blue side is the blue side even if ONLY the center dot is blue.

Which side is the TOP, FRONT, LEFT, RIGHT, BACK, or BOTTOM is entirely dependent on how
you are holding the cube at the time.  The assumption is always that you are looking at
the cube face-on, with FRONT facing you, BACK being the side opposite that, and LEFT,
RIGHT, TOP, and BOTTOM being fairly self-explanatory from there.

Individual pieces are designated by SIDE-EDGE-PLACE, so TOP-LEFT-MIDDLE is the piece
located on the TOP side, on the LEFT edge of the side, in the MIDDLE position.

For the sake of brevity, CW = clockwise and CCW = counter-clockwise.  When describing
CW/CCW rotations, the rotation is always directed as if you were viewing that side
face-on.  I.e. - as if you were holding the cube with that side as the FRONT.

Key to the cube "diagrams" (if you'll excuse the exaggeration):
<dl>
    <dt>X</dt>
    <dd>That is to say, any single letter.  One specific color on the entire cube.  So for
        example an &quot;A&quot; would stand for one particular color, and would be that
        same color across all the sides in a particular diagram.  Unless otherwise noted,
        a specific letter probably won't refer to the same color from diagram to
        diagram.</dd>
    <dt>.</dt>
    <dd>A placeholder to mark a spot whose color doesn't matter in the context of that
        diagram.</dd>
</dl>


## Steps

1. Solve one face such that each of the edges is the same color as its respective face's
   center dot.  There's no particular algorithm for this; you're just solving a single
   side but also paying attention to the secondary colors on each piece that you move into
   position.

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   A A A  B B B  C C C  D D D  E E E  . . .
   A A A  . B .  . C .  . D .  . E .  . . .
   A A A  . . .  . . .  . . .  . . .  . . .
   ```

1. Move the middle side pieces to their correct spots.  See "Completing The Second Row" in
   the Algorithms section.  You will use that algorithm once for each piece that needs to
   be moved into its place.

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   A A A  B B B  C C C  D D D  E E E  . . .
   A A A  B B B  C C C  D D D  E E E  . . .
   A A A  . . .  . . .  . . .  . . .  . . .
   ```

1. Turn the cube over so that the old TOP is now the BOTTOM.  You will now make a "plus"
   on the new TOP, using the FRU-RUF algorithm.

   You want the cube to be oriented such that it looks like one of the following patterns
   (in order of preference):

   ```
   TOP                TOP                      TOP              TOP
   . . .              . . .                    . . .            . . .
   . A .  or, better  . A A  or, still better  . A A  or, best  A A A
   . . .              . . .                    . A .            . . .
   ```

   Orient the cube in your hand so that the TOP resembles the best one of those that it
   can, and then use FRU-RUF.  If it's still not a "plus" when you finish (see diagram
   below), once again re-orient it so it looks like the best of the above shapes that it
   can, and use FRU-RUF again.  Repeat that process until you get the "plus".

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   . A .  . . .  . . .  . . .  . . .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

1. Move the "plus"'s ends such that they're aligned with their correct sides, using
   combinations of RU2 and/or LU2.

   You *may* get lucky and the cube already looks like the desired result after the
   previous step.  In the majority of cases, the cube will be in one of the following
   positions instead.  Note that you may have to rotate the TOP side and/or re-orient the
   cube to make it look exactly like one of these.

   ```
   1. Two opposite sides are correct, the other two are swapped.

   TOP    FRONT  LEFT   BACK   RIGHT
   . A .  . B .  . E .  . D .  . C .
   A A A  B B B  C C C  D D D  E E E
   . A .  B B B  C C C  D D D  E E E
   ```

   ```
   2. Two adjacent sides are correct, the other two are swapped.

   TOP    FRONT  LEFT   BACK   RIGHT
   . A .  . B .  . C .  . E .  . D .
   A A A  B B B  C C C  D D D  E E E
   . A .  B B B  C C C  D D D  E E E
   ```

   ```
   3. One side is correct, the others are all wrong.

   TOP    FRONT  LEFT   BACK   RIGHT
   . A .  . B .  . E .  . C .  . D .
   A A A  B B B  C C C  D D D  E E E
   . A .  B B B  C C C  D D D  E E E
   ```

   Your goal for positions 1 and 2 are to change them to position 3.

   For position 1:

   1. Re-orient the cube so that the opposite **correct** sides are RIGHT and LEFT.
   1. Use RU2 once.
   1. Rotate TOP 90' CW.
   1. At this point, one edge piece on the cube should be aligned with its correct side.
      I.e. - The cube should now be in position 3.

   For position 2:

   1. Re-orient the cube so that the adjacent **correct** sides are RIGHT and BACK.
   1. Use RU2 once.
   1. Rotate TOP 90' CW.
   1. At this point, one edge piece on the cube should be aligned with its correct side.
      I.e. - The cube should now be in position 3.

   For position 3:

   1. Orient the cube so that the side with the **correct** colored edge piece is FRONT.
   1. Check the BACK-TOP-MIDDLE piece.  Does the color on the BACK side of that piece need
   to move to the LEFT or RIGHT side?
      - If it needs to move to the LEFT side, use LU2.
      - If it needs to move to the RIGHT side, use RU2.

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   . A .  . B .  . C .  . D .  . E .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

1. Manipulate the corner pieces until there's at least one corner in its correct spot,
   using LURU2.

   The cube should now look like the following diagram, but with the condition that at
   least one of the TOP corners' colors should be the same colors as all of its
   corresponding sides, even if they're not in the correct orientation.  Example: Let's
   say TOP is blue, RIGHT is white, and BACK is red.  If the corner piece adjacent to all
   three of those sides (in other words, the TOP-RIGHT-BACK corner) is the red+white+blue
   corner piece, the condition is fulfilled, regardless of whether the white face of the
   piece is on the RIGHT side of the cube at this point.

   If the cube is already in this state after the previous step, you can skip this step.

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   . A .  . B .  . C .  . D .  . E .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

1. If **all** of the TOP corner pieces are positioned such that their colors correspond to
   the sides they're adjacent to, even if the orientation is off, you can skip this step.
   E.g. - The red+white+blue corner piece is in the corner adjacent to the red, white, and
   blue sides, regardless of whether each color is facing its corresponding side.  If all
   the TOP corner pieces are like that, you can skip this step.

   Otherwise, hold the cube such that the corner piece that is in its correct spot is in
   the TOP-RIGHT-FRONT position.  Use LURU2 repeatedly from this position until the
   remaining corners are all in their correct places (color-wise) as well.  Orientation
   still doesn't matter at this point.  None, some, or even all of the corners may be
   correctly oriented.

   The cube should now look like this, but all of the TOP corner pieces should be
   positioned as described above:

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   . A .  . B .  . C .  . D .  . E .  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   . A .  B B B  C C C  D D D  E E E  F F F
   ```

   So TOP-FRONT-LEFT should be colored {A,B,C} (in some order), TOP-FRONT-RIGHT should be
   {A,B,E}, TOP-BACK-LEFT should be {A,C,D}, and TOP-BACK-RIGHT should be {A,D,E}.

1. Use RU2+LU2 to rotate the corners into their final correct orientations.

   The RU2+LU2 algorithm rotates both TOP-RIGHT corner pieces at once, leaving the rest of
   the cube untouched.  So you'll want to orient the cube such that one or both of those
   corners are misaligned, and then execute the algorithm once or twice until at least one
   of them is aligned correctly (doing it three times returns you to your original state).
   You may need to re-orient the cube and repeat this process a couple of times until all
   the corners are correct.

   The cube should now look like this:

   ```
   TOP    FRONT  LEFT   BACK   RIGHT  BOTTOM
   A A A  B B B  C C C  D D D  E E E  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   A A A  B B B  C C C  D D D  E E E  F F F
   ```

1. Bask in the glow of your intellectual prowess.


## Algorithms

General Notes

* In the short forms below, "U" stands for "Upper", which would be "TOP" in the diagrams.
  Using "U" just injected a vowel in the acronyms, which made them somewhat pronouncable
  and helped them stick in my brain when I was learning them.  `:)`  YMMV.
* X  = Rotate side X 90' CW    (ex: R  == rotate the RIGHT side 90' CW)
* X' = Rotatate side X 90' CCW (ex: R' == rotate the RIGHT side 90' CCW)
* As it happens, the BACK side is never manipulated in the algorithms.  So if a "B"
  appears in an algorithm's short form, that stands for BOTTOM.

---

### Completing The Second Row

There are three possible positions you can be in.  Note that you may need to rotate the
BOTTOM side 90-180' in order to get to one of them exactly.

```
1. The piece that belongs in the FRONT-RIGHT-MIDDLE position is in the
   FRONT-BOTTOM-MIDDLE position.
FRONT  RIGHT  BOTTOM
A A A  B B B  . B .
. A .  . B .  . . .
. A .  . . .  . . .
```

```
2. The piece that belongs in the FRONT-LEFT-MIDDLE position is in the
   FRONT-BOTTOM-MIDDLE position.
LEFT   FRONT  BOTTOM
A A A  B B B  . A .
. A .  . B .  . . .
. . .  . B .  . . .
```

```
3. The piece that belongs in the FRONT-RIGHT-MIDDLE position is there,
   but is oriented backwards.
FRONT  RIGHT
A A A  B B B
. A B  A B .
. . .  . . .
```

No matter which position you start in, you will end up with this:

```
FRONT  RIGHT
A A A  B B B
. A A  B B .
. . .  . . .
```

#### Starting From Position 1

Short form: **B'R'BRBFB'F'**

Long form:

1. Rotate BOTTOM 90' CCW
1. Rotate RIGHT 90' CCW
1. Rotate BOTTOM 90' CW
1. Rotate RIGHT 90' CW
1. Rotate BOTTOM 90' CW
1. Rotate FRONT 90' CW
1. Rotate BOTTOM 90' CCW
1. Rotate FRONT 90' CCW


#### Starting From Position 2

Short form: **BLB'L'B'F'BF**

Long form:

1. Rotate BOTTOM 90' CW
1. Rotate LEFT 90' CW
1. Rotate BOTTOM 90' CCW
1. Rotate LEFT 90' CCW
1. Rotate BOTTOM 90' CCW
1. Rotate FRONT 90' CCW
1. Rotate BOTTOM 90' CW
1. Rotate FRONT 90' CW


#### Starting From Position 3

Here you will move the piece such that you end up with Position 1 and then use that
algorithm to move it to its final place.

Short form: **R'BRBFB'F'BB**

Long form:

1. Rotate RIGHT 90' CCW
1. Rotate BOTTOM 90' CW
1. Rotate RIGHT 90' CW
1. Rotate BOTTOM 90' CW
1. Rotate FRONT 90' CW
1. Rotate BOTTOM 90' CCW
1. Rotate FRONT 90' CCW
1. Rotate BOTTOM 90' CW
1. Rotate BOTTOM 90' CW

---

### FRU-RUF

Short form: **FRUR'U'F'**

Long form:

1. Rotate FRONT 90' CW
1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CW
1. Rotate RIGHT 90' CCW
1. Rotate TOP 90' CCW
1. Rotate FRONT 90' CCW


Use repeatedly to form the "plus".

Creates this...

```
TOP
. A .
A A A
. A .
```

---


### LURU2

Short form: **L'URU'LUR'U'**

Long form:

1. Rotate LEFT 90' CCW
1. Rotate TOP 90' CW
1. Rotate RIGHT 90' CW
1. Rotate TOP 90' CCW
1. Rotate LEFT 90' CW
1. Rotate TOP 90' CW
1. Rotate RIGHT 90' CCW
1. Rotate TOP 90' CCW


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

Where X, Y, and Z refer to the same PIECES (**not** colors!) between those two diagrams.

---


### RU2

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

---


### LU2

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


Moves TOP-LEFT-MIDDLE, TOP-BACK-MIDDLE, and TOP-RIGHT-MIDDLE one place CW on the TOP side.

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

---


### RU2+LU2

Steps: Execute **RU2** and **LU2** consecutively (either order works).


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
