## Introduction

In order to accommodate 2D effects we have modified how Segment settings are used and added 2D Matrix and panel variables on the [Led Preferences](https://github.com/atuline/WLED/wiki/LED-Preferences) settings.
Note: Currently only working in dev. You are invited to test this and give feedback on [Beta testing discord channel](https://discord.com/channels/700041398778331156/700701772838207640)

## 2D architecture

WLED SR distinguishes between the following levels
* 2D Segment (dev)
* 2D Matrix (dev)
* 2D Panel (dev)

An effect is plotted on a segment. A segment is a rectangle on a matrix (0,0 is always topright, logical level). A matrix is implemented by one or more identical led panels, each with a specific layout (e.g. first led bottom left, serpentine, physical level).

Note: 2D effects can also be projected on a 1D LED Strip instead of a 2D Panel. e.g. for a led strip of 144 leds you can define width=height=12 and each zone of 12 leds is a row of a matrix. Rows are then side by side instead of above each other. Some 2D effects, e.g. graphic equalizer look still pretty cool on strips (as is the other way around with 1D effects on a 2D matrix like NoiseMove or Sparkle).

## 2D Segments
As WLED supports multiple segments, all effects and therefore also 2D effects are first projected on a segment. In [1D, a segment is a zone on a LED strip](https://github.com/Aircoookie/WLED/wiki/Segments) and is specified by Start Led and a Stop Led.
In 2D, a segment is a rectangle on a 2D matrix and 2D effects plot on this rectangle using x,y coordinates of the SEGMENT.
A rectangle can be defined in the Segment UI where the start led specifies the top-left and the stop led specifies the bottom-right of the rectangle.
Segments can overlap. In fact overlapping creates very nice effects.

### Rotation and Mirroring
A segment can be rotated 90º degrees and mirrored vertical or horizontal. The spacing variable of a segment is temporary used for this. In the future separate variables could be added on segments to replace this.

Enter a value between 0 and 7 into the spacing variable of a segment to obtain the following effects: 

Value | Binary | Rotation | Vertical Mirror | Horizontal Mirror
|---|---|---|---|---|
0|000|-|-|-|no rotation or mirroring => equals 0º rotation


0 (000):      - + - + - => no rotation or mirroring => equals 0º rotation

1 (001):      - + - + Mirror Horizontal 

2 (010):      - + Mirror Vertical + -

3 (011):      - + Mirror Vertical+ Mirror Horizontal=> equals 180º rotation

4 (100):      rotation + - + - => equals 90º rotation

5 (101):      rotation + - + Mirror Horizontal

6 (110):      rotation + Mirror Vertical+ -

7 (111):      rotation + Mirror Vertical+ Mirror Horizontal=> equals 270º rotation

### Examples
To get the (x,y) coordinates from the start and stop led:
* Segment top left = (start%matrixWidth, start/matrixWidth)
* Segment bottom right = (stop%matrixWidth, stop/matrixWidth)

Example of 1 segment (default) covering a whole 16x16 matrix:
* start = 0, stop = 255
* top left = (0,0)
* bottom right = (15,15)
* width = height = 16

Example of a segment covering a middle part rectangle of the 16x16 matrix:
* start = 20, stop = 235
* top left = (4,1)
* bottom right = (10,14)
* width = 7
* height = 14

Example of a segment covering the left part of the 16x16 matrix:
* start = 0, stop = 241
* top left = (0,0)
* bottom right = (0,15)
* width = 1
* height = 16

Multiple segments can be specified this way

## 2D Matrices and panels

See [Led Preferences](https://github.com/atuline/WLED/wiki/LED-Preferences)

## Technical

* CRGB leds[MAX_LEDS+1]; in FX.cpp defines all leds on the matrix. Multiple segments share this array and effects should only write to leds[] within the boundaries of a segment. This is done by calling leds[XY(x,y)] or leds[realPixelIndex(i)].
* Functions with leds as parameter should make sure to follow above rule and have been refactored for this. E.g. fadeToBlackBy(leds, 32) or fill_solid(leds, 0) otherwise it writes outside the segment boundaries. 

## Examples

### 16 x 12 matrix

matrixWidth = 16, matrixHeight = 12.

Total led count 192 leds

left and right binmap effect. In the middle noisemove.

* Segment 0 (middle): start=1, stop=191, effect=noisemove
* Segment 1 (left): start=0, stop=176, effect=binmap
* Segment 2 (right): start=15, stop=192, effect=binmap

## HTML in wiki?

<form onsubmit="return false" oninput="    totalamount.value = Math.round(principal.value * (Math.pow((1 + interest.value / 100), period.value)) * 100) / 100;">

            Principal<input name="principal" id="principal" type="number">

            <br />

            Duration<input name="period" id="period" type="number">

            <br />

            Interest Rate<input name="interest" id="interest" type="number">

            <br />

            Total amount <output name="totalamount" id="totalamount" for="principal period interest"></output>

        </form>