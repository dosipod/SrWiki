See [WLED General settings](https://github.com/aircoookie/WLED/wiki/Settings)



### LED settings
See [WLED General Led Settings](https://github.com/aircoookie/WLED/wiki/Settings#led-settings)

#### Additional Sound Reactive Settings
2D Matrix and Panels

Setting name | Value Range | Description
|---|---|---|
Matrix Width x Height | 1..x | Dimensions of 2D Matrix. width x height should match LED count!
Serpentine | Y/N | Select if your layout is serpentine. Otherwise, it's not. (dev version)
Rowmajor| Y/N | Select if your layout is horizontal. De-select if it's vertical. (dev version)
Flipmajor| Y/N | Flip the major axis, ie top to bottom if it's a horizontal layout. (dev version)
Flipminor| Y/N | Flip the minor axis, ie left to right if it's a horizonal layout. (dev version)
Transpose| Y/N | Swap the major and the minor axes (otherwise no swap). Don't use on non-square. (dev version)
Multiple panels | Y/N | Check if more than 1 panel, e.g. 4 8x32 or 16x16 panels. Multiple panels are connected together starting top left and ending bottom right (dev version)
Horizontal / Vertical panels | 1..x | Number of panels on horizontal and vertical axis. Total panels is horizontal x vertical. Total Width and Height of connected panels should match Matrix Width and Height (dev version)

Note 1: The number of LED's should contain ALL the number of ALL LED's in the display.
Note 2: The 2D matrix value should contain values for number of pixels in all your connected panels.

Example: 

I have 6 - 8x32 panels. They are connected:

0 1 2
3 4 5


![6 - 8x32 panels](https://github.com/atuline/WLED/blob/assets/media/panels.jpg?raw=true)


•	If you only have 1 led panel of 16x16, then you ‘must’ set total led count to 256 and width and height to 16. It does not make sense to check multiple panels then because you do not have multiple panels. But you can do it, for instance 4 horizontal and 4 vertical, than the 16x16 panel will be divided in 4 areas of 4x4 pixels but the panel functionality assumes that the first panel is top left, expanding right, then down and the last is bottom right and that is not the case in 1 led panel. So it does not look good.
•	So for multiple panels to work, you physically need multiple panels, which are connected in series. Do you have a second 16x16 panel? Then you can set horizontal to 2 and vertical to 1 If you put them side by side (32x16), or vice versa if you put them above eachother (16x32)
So I need to think how to explain this better. See my first attempt here: https://github.com/atuline/WLED/wiki/2D-Functionality.
What do you think after reading the remarks I make here. If this matches what you did, then I can add something like this:
•	Total leds should be the sum of all leds of all panels
•	Matrixwidth and height should be the width and height of all panels together.
•	If you specify multiple panels you should physically have multiple panels which are connected together 

