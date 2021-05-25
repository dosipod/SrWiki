**Note 1:** Due to its limited capability, we have disabled 2D animations on the ESP8266 platform.    
**Note 2:** The 2D routines require a minimum of 4 pixels in both directions. If you see blinking red, your 2D settings don't match the requirements.    
**Note 3:** As we continue to develop SR WLED, some animations may appear or disappear. It's still a work very much in progress. Some may only appear in the dev branch for now.    


| Effect | Description | Sliders
| --- | --- | ---
| Flow Stripe |Strip with rotating colours.|Speed: Controls a speed timer <br/>Intensity: Controls another timer
| Perlin Move |Using Perlin Noise for movement.|Speed: Speed of elements<br/>Intensity: # of pixels<br />fft low: Fade rate
|    |  |  <br />
| 2D Black Hole | Stars moving around black hole. |fft low: one beat<br/>fft high: Another beat<br/>fft custom: last beat
| 2D Colored Bursts |Multiple lines.|Speed: Speed of lines<br/>Intensity: Number of lines
| 2D DNA | A very cool DNA like pattern. Select a palette.|Speed: Scroll speed<br />Intensity: Blur
| 2D DNA Spiral |Spiraling DNA pattern.|Speed: Speed.<br/>Intensity: Frequency
| 2D Drift |A rotating caleidoscope.|Speed: Speed of rotation.<br/>Intensity: Blur
| 2D Fire2012| Mark Kriegsman's fire routine.|n/a
| 2D Firenoise |Using Perlin Noise for fire.|Speed: Yscale.<br/>Intensity: Scale
| 2D Frizzles |Moving patterns.|Speed: One thing<br/>Intensity: Another thing
| 2D Gameoflife |Scrolling game of life.|Speed: Speed <br/>Intensity: Starting grid
| 2D Hiphotic | A moving plasma.|Speed: One direction<br/>Intensity: Other direction
| 2D Lissajous | A frequency based Lissajous pattern.|Speed: Frequency of cos<br/>Intensity: Frequency of sin
| 2D Matrix |The Matrix in 2D.|Speed: Affects the speed of the movement<br />Intensity: Number of lines
| 2D Meatballs |A cool plasma type effect.|n/a
| 2D Plasma |A plasma effect.|Speed: Affects the speed of the movement<br />fft low: Shifts the colours<br />fft high: Distance from the plasma
| 2D Plasma Ball |A ball of plasma. |Speed: Speed. <br/>Intensity:
| 2D Polar Lights |The northern lights.|Speed: Speed.<br/>Intensity: Frequency.<br/>fft low: Palette rotation
| 2D Pool Noise |Looking at a pool.|n/a
| 2D Pulser |Travelling waves.|Speed: Speed. <br/>Intensity: Blur
| 2D Sindots |Moving/rotating pattern.|Speed: Speed. <br/>Intensity: Length/size
| 2D Squared Swirl |Boxes moving around.|fft3: Blur amount
| 2D Sun radiation |The sun! Doesn't support segments.|Speed: Variance<br/>Intensity: Brightness
| 2D Twister |A large twister.|Speed: Speed <br/>Intensity: Phases

### 2D Clock Overlay

To configure, go to Time & Macros setting

Time setup: fill in required parameters

Clock: Clock overlay; Analog Clock, check Show 5min marks, uncheck the rest



### Thanks are in order

Oh, and special thanks are in order for urish for creating wokwi, Elliot and his team for soulmatelights and Stepko and ldirko for some awesome 2D animations. With their approval, we were able to convert and publish several of their animations to use with WLED.
