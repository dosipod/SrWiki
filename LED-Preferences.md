
## LED Preferences for Sound Reactive WLED

The sound reactive fork of WLED support multiple layouts of a 2D matrix led panel. In addition it support multiple 2D matrix led panels.

![6 - 8x32 panels](https://github.com/atuline/WLED/blob/assets/media/panels1.jpg?raw=true)

## 2D Matrix Settings (how each panel is laid out)

A matrix is made of 1 or more identical physical led panels connected together. Width and Height is the sum of leds in all the panels in both directions.

Animations are written so that the first LED in the matrix is in the top left corner. If your matrix is oriented in a different fashion, you can use the 2D Panel layout settings to adjust that.




| Setting name | Value Range | Description
| --- | --- | ---
Serpentine | Y/N | Select if your layout is serpentine. Otherwise, it's not. (dev version)
Transpose| Y/N | Swap the major and the minor axes (otherwise no swap). Don't use on non-square. (dev version)

**Note:** If multiple panels are used, they must be identical.

### Multiple Panels Settings (the number of LED panels)


| Setting name | Value Range | Description
| --- | --- | ---
Multiple panels | Y/N | Check if more than 1 panel, e.g. 4 8x32 or 16x16 panels. Multiple panels are connected together starting top left and ending bottom right (dev version)
Horizontal / Vertical panels | 1..x | Number of panels on horizontal and vertical axis. Total panels is horizontal x vertical. Total Width and Height of connected panels should match Matrix Width and Height (dev version)


**Note 1:** The number of LED's should contain ALL the number of ALL LED's in the display.
**Note 2:** The 2D matrix value should contain values for number of pixels in all your connected panels.

## Example: 

I have 6 - 8x32 panels. They are connected sequentially with 32 led's wide and 8 led's high as follows:

0 1 2

3 4 5




