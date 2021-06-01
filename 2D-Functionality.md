## 2D functionality
* An `XY()` function which returns the index number of the X-Y coordinate on the matrix has been added.
  * The origin (x=0,y=0) is at the top left of the display, with X axis extending to the right, Y axis toward the bottom.
  * The LED order starts from 0 at the top left, and ascends to the right on the top row.
  * 2D addressing is leds[XY(column, row)]
* A serpentine/zig-zag setting has been added to 'LED Settings'.
  * With serpentine mode enabled, the led index on every odd row (top row is row 0) is ascending from right to left, and on even rows is ascending from left to right
  * The opposite of serpentine is "progressive", where all rows are oriented in ascending order from left to right

As documented in [FastLED](https://github.com/FastLED/FastLED/blob/master/examples/XYMatrix/XYMatrix.ino), leds[0] should end up being at the top left of your array:

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
  * It's likely that there will at least a minor change in animations required to support a non-rectangular or non-contiguous mapping.

### XY() routine update

The dev branch has a new XY() function (thanks Sutaburosu) in FX.cpp, which supports multiple layouts.

There are 5 orientation flags as follows:

*  ROWMAJOR   - Select if your layout is horizontal. De-select if it's vertical.
*  SERPENTINE - Select if your layout is serpentine. Otherwise, it's not.
*  FLIPMAJOR  - Flip the major axis, ie top to bottom if it's a horizontal layout.
*  FLIPMINOR  - Flip the minor axis, ie left to right if it's a horizonal layout.
*  TRANSPOSE  - Swap the major and the minor axes (otherwise no swap). Don't use on non-square.

By comparison, the author's aliexpress purchased 16x16 array needs to be configured as:

```
Serpentine | Rowmajor | Flipmajor
```

**Note:** When an X,Y value goes out of bounds, this routine writes to an LED beyond SEGLEN, and as a result, we need to use the setPixels() routine to write to the display.

**Note:** Working with this can be confusing, so here's a simulator you can play around with to get familiar with[ XY()  at Wokwi](https://wokwi.com/arduino/projects/298774787561357832).