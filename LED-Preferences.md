
## LED Preferences for Sound Reactive WLED

The sound reactive fork of WLED supports multiple layouts of a 2D matrix led panel as well as multiple identical 2D matrix led panels.

![6 - 8x32 panels](https://github.com/atuline/WLED/blob/assets/media/panels1.jpg?raw=true)

### 2D Matrix
2D effects are projected on a 2 dimensional matrix. 

A specific led is identified by led[x,y] where led[0,0] is in the top left corner (logical layer)

Setting name | Value Range | Description | Master/Dev
|---|---|---|---|
Width| 1..x | Width of the matrix | Master
Height| 1..y | Height of the matrix | Master

Note: width x height should match LED count! 

### 2D Panels
A matrix is made of 1 or more identical physical led panels (physical layer)
Setting name | Value Range | Description | Master/Dev
|---|---|---|---|
Multiple panels| Y/N | No if only one panel, yes if more than one | Dev
Horizontal panels| 1..x | Number of panels side by side | Dev 
Vertical panels| 1..y | Number of panels above each other | Dev

Note: Panel width = matrix width / horizontal panels and panel height = matrix height / vertical panels

Note: Total panels = horizontal * vertical

### 2D Panel layout
Specify how a led panel is wired.

This is used to translate the logical layer (led[x,y]) to the physical layer (led[0] .. led[n]). 

Animations are written so that the first LED in in the panel(s) is in the top left corner. If your panels are oriented in a different fashion, you can use the 2D Panel layout settings to adjust that.

Setting name | Value Range | Description | Master/Dev
|---|---|---|---|
First led position| Top/Bottom & Left/Right | Where is the first led positioned | Dev (replacing flipmajor/minor)
Orientation| Horizontal / Vertical | Are rows of leds wired horizontal or vertical | Dev (replacing rowMajor)
Serpentine| Y/N | Are rows of leds wired zig-zag or not | Master
Transpose| Y/N | Swap the axes (otherwise no swap). Don't use on non-square panels | Dev

**Note:** If multiple panels are used, they must be identical.

### Example: 

I have 6 - 8x32 panels. They are connected sequentially with 8 led's wide and 32 led's high as follows:

0 1 2

3 4 5

**Note:** Working with this can be confusing, so here's a simulator you can play around with to get familiar with[ XY()  at Wokwi](https://wokwi.com/arduino/projects/298774787561357832).



