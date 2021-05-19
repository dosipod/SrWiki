## 2D functionality
* An `XY()` function which returns the index number of the X-Y coordinate on the matrix has been added.
  * The origin (x=0,y=0) is at the top left of the display, with X axis extending to the right, Y axis toward the bottom.
  * The LED order starts from 0 at the top left, and ascends to the right on the top row.
  * 2D addressing is leds[XY(column, row)]
* A serpentine/zig-zag setting has been added to 'LED Settings'.
  * With serpentine mode enabled, the led index on every odd row (top row is row 0) is ascending from right to left, and on even rows is ascending from left to right
  * The opposite of serpentine is "progressive", where all rows are oriented in ascending order from left to right

```
Don't enable serpentine setting if your pixels are
laid out all running the same way, like this:

    0 >  1 >  2 >  3 >  4
                        |
    .----<----<----<----'
    |
    5 >  6 >  7 >  8 >  9
                        |
    .----<----<----<----'
    |
   10 > 11 > 12 > 13 > 14
                        |
    .----<----<----<----'
    |
   15 > 16 > 17 > 18 > 19

Enable serpentine setting if your pixels are
laid out back-and-forth, like this:

    0 >  1 >  2 >  3 >  4
                        |
                        |
    9 <  8 <  7 <  6 <  5
    |
    |
   10 > 11 > 12 > 13 > 14
                       |
                       |
   19 < 18 < 17 < 16 < 15

```

* `matrixWidth` and `matrixHeight` are new 'LED Settings'.
  * `matrixWidth` is the number of pixels per row.
  * `matrixHeight` is the number of pixels per column.
* Some existing animations (as of Jan 2021) were coded for different orientations and need to be redone to match the newly agreed to orientation described above.
* Not yet supported: rotation, or any mapping other than rectangular progressive/serpentine.
  * Ideally the `XY()` function will return the correct led index even with a rotated display, and `matrixWidth`/`matrixHeight` will refer to the rotated display's dimensions.
  * It's likely that there will at least a minor change in animations required to support a non-rectangular or non-contiguous mapping.

### Array Layouts
* Top left to right (is the default above)
* Top right to left
* Bottom left to right (aliexpress boards)
* Bottom right to left

For both serpentine and non-serpentine layouts.

This could either be in the XY() routine or in setPixels(). Will need to review both.

