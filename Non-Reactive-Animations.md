**Note 1:** Due to its limited capability, we have disabled 2D animations on the ESP8266 platform, although those settings still show up in the LED settings UI.  
**Note 2:** If you are using 2D, please ensure your 2D settings are correct. We aren't checking them.  
**Note 3:** Some 2D routines require a minimum of 4 pixels in both directions. You may get a red blinking pattern if too small.
**Note 4:** If your Total # of LED's is less than your 2D settings, then you may get blinking red LED's instead of the pattern.


| Effect | Description | Sliders
| --- | --- | ---
| Flow Stripe |Strip with rotating colours.|Speed: Controls a speed timer <br/>Intensity: Controls another timer
| Perlin Move |Using Perlin Noise for movement.|Speed: Speed of elements<br/>Intensity: # of pixels<br />fft1: Fade rate
|    |  |  <br />
| 2D CA Elementary |Scrolling game of life.|Speed: Speed <br/>Intensity: Starting grid.
| 2D Colored Bursts |Multiple lines.|Speed: Speed of lines.<br/>Intensity: Number of lines.
| 2D DNA | A very cool DNA like pattern. Select a palette.|Speed: Scroll speed.<br />Intensity: Blur.
| 2D DNA Spiral |Spiraling DNA pattern.|Speed: Speed.<br/>Intensity: Frequency.
| 2D Drift |A rotating caleidoscope.|Speed: Speed of rotation.<br/>Intensity: Blur.
| 2D Fire2012| Mark Kriegsman's fire routine.|n/a
| 2D Firenoise |Using Perlin Noise for fire.|n/a
| 2D Frizzles |Moving patterns.|Speed: One thing.<br/>Intensity: Another thing.
| 2D Hiphotic | A moving plasma.|Speed: One direction.<br/>Intensity: Other direction.
| 2D Julia |An animated Julia set |Intensity: max # of calculations per pixel.<br />fft1: x center of the set.<br />fft2: y center of the set.<br /> fft3: Size of the window.
| 2D Lissajous | A frequency based Lissajous pattern.|Speed: Frequency of cos,<br/>Intensity: Frequency of sin.
| 2D Matrix |The Matrix in 2D.|Speed: Affects the speed of the movement.<br />Intensity: Number of lines.<br/>fft3: Change orientation.
| 2D Meatballs |A cool plasma type effect.|n/a
| 2D Plasma |A plasma effect.|Speed: Affects the speed of the movement.<br />fft1: Shifts the colours.<br />fft2: Distance from the plasma.
| 2D Plasma Ball |A ball of plasma. |Speed: Speed. <br/>Intensity:
| 2D Polar Lights |The northern lights.|Speed: Speed.<br/>Intensity: Frequency.<br/>fft1: Palette rotation.
| 2D Pool Noise |Looking at a pool.|n/a
| 2D Pulser |Travelling waves.|Speed: Speed. <br/>Intensity: Blur.
| 2D Sindots |Moving/rotating pattern.|Speed: Speed. <br/>Intensity: Length/size.
| 2D Squared Swirl |Boxes moving around.|fft3: Blur amount
| 2D Sun radiation |The sun!|n/a
| 2D Twister |A large twister.|Speed: Speed. <br/>Intensity: Phases.

### 2D Julia notes

This animation supports palettes. fft1-3 affect the rate of **change** of size/location rather than just changing the size/location. fft3 controls the window size, where the midpoint keeps the window the same size, while a value to the left continuously makes the window smaller, and larger to the right.
How to reset this animation? Just center the sliders, click another animation and then select this one again. Feel free to PR a different control layout (along with associated documentation). We get to use up to 5 sliders.

### Thanks are in order

Oh, and special thanks are in order for urish for creating wokwi, Elliot and his team for soulmatelights and Stepko and ldirko for some awesome 2D animations. With their approval, we were able to convert and publish several of their animations to use with WLED.
