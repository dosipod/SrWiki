
## AirCoookie's LED settings
See [WLED General Led Settings](https://github.com/aircoookie/WLED/wiki/Settings#led-settings)

## LED Settings for Sound Reactive additions

The sound reactive fork of WLED support multiple 2D layouts as well as multiple panels.


## 2D Matrix Settings


| Setting name | Value Range | Description
| --- | --- | ---
Matrix Width x Height | 1..x | Dimensions of 2D Matrix. width x height should match LED count!
Serpentine | Y/N | Select if your layout is serpentine. Otherwise, it's not. (dev version)
Rowmajor| Y/N | Select if your layout is horizontal. De-select if it's vertical. (dev version)
Flipmajor| Y/N | Flip the major axis, ie top to bottom if it's a horizontal layout. (dev version)
Flipminor| Y/N | Flip the minor axis, ie left to right if it's a horizonal layout. (dev version)
Transpose| Y/N | Swap the major and the minor axes (otherwise no swap). Don't use on non-square. (dev version)



### Multiple Panels


| Setting name | Value Range | Description
| --- | --- | ---
Multiple panels | Y/N | Check if more than 1 panel, e.g. 4 8x32 or 16x16 panels. Multiple panels are connected together starting top left and ending bottom right (dev version)
Horizontal / Vertical panels | 1..x | Number of panels on horizontal and vertical axis. Total panels is horizontal x vertical. Total Width and Height of connected panels should match Matrix Width and Height (dev version)


Note 1: The number of LED's should contain ALL the number of ALL LED's in the display.
Note 2: The 2D matrix value should contain values for number of pixels in all your connected panels.

### Example: 

I have 6 - 8x32 panels. They are connected sequentially:

0 1 2

3 4 5


![6 - 8x32 panels](https://github.com/atuline/WLED/blob/assets/media/panels.jpg?raw=true)

