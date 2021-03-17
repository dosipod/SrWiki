**Note 1:** Due to its limited capability, we have disabled 2D animations on the ESP8266 platform, although those settings still show up in the LED settings UI.  
**Note 2:** If you are using 2D, please ensure your 2D settings are correct. We aren't checking them.  
**Note 3:** Some 2D routines require a minimum of 4 pixels in both directions.  
**Note 4:** If your Total # of LED's is less than your 2D settings, then you may get blinking red LED's instead of the pattern. This is a programed error reporting function.


| Effect | Description | Sliders
| --- | --- | ---
| Perlin Move | Using Perlin Noise for movement. | Speed: Speed of elements<br/>Intensity: # of pixels<br />fft1: Fade rate
| 2D DNA | A very cool DNA like pattern by /u/ldirko. | n/a
| 2D Fire2012 | Mark Kriegsman's fire routine. | n/a
| 2D Firenoise | Using Perlin Noise for fire. | n/a
| 2D Julia | An animated Julia set | Intensity: max # of calculations per pixel <br /> fft1: x center of the set <br /> fft2: y center of the set <br /> fft3: Size of the window
| 2D Matrix | The Matrix in 2D. | Speed: Affects the speed of the movement. <br /> fft3: Change orientation
| 2D Meatballs | A cool plasma type effect by Stefan Petrick. | n/a
| 2D Plasma | A plasma effect. | Speed: Affects the speed of the movement. <br />  fft1: Shifts the colours <br />fft2: Distance from the plasma
| 2D Squared Swirl | Boxes moving around. | fft3: Blur amount

### 2D Julia notes

This animation supports palettes. fft1-3 affect the rate of **change** of size/location rather than just changing the size/location. fft3 controls the window size, where the midpoint keeps the window the same size, while a value to the left continuously makes the window smaller, and larger to the right.
How to reset this animation? Just center the sliders, click another animation and then select this one again.

Feel free to PR a different control layout (along with associated documentation). We get to use up to 5 sliders.

