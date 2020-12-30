
Effects beginning with '*' are volume only and run on both ESP32 and ESP8266. They also have a 'Squelch', or background noise setting near the bottom of the LED settings page. 

Effects beginning with '**' use FFT (Fast Fourier Transforms) for frequency detection and only run on the ESP32.

Some of the 2D routines require 256 LED's in a 16x16 matrix.


| Effect | Description | Sliders
| :------------------ | --- | ---
| *Gravcenter | Volume reactive vu-meter from center with gravity and perlin noise. | Speed: Rate of fall <br /> Intensity: Sensitivity
| *Gravcentric |  Volume reactive vu-meter from center with gravity. Volume provides index to (time rotating) palette colour. | Speed: Rate of fall <br /> Intensity: Sensitivity
| *Gravimeter | Volume reactive vu-meter with gravity and perlin noise. | Speed: Rate of fall <br /> Intensity: Sensitivity
| *Juggles | Juggling balls.| Speed: Yes <br /> Intensity: # of balls
| *Matripix | Similar to Matrix. | Speed: yes <br /> Intensity: Brightness
| *Midnoise | Perlin noise emanating from center.| Speed: Fade rate <br /> Intensity: Maximum length
| *Noisefire | A perlin noise based volume reactive fire routine. | n/a
| *Noisemeter | Volume reactive vu-meter. | Speed: Fade rate <br /> Intensity: Width
| *Pixels | Random pixels. | Intensity: # of pixels
| *Pixelwave | Pixels emanating from center. | Speed: yes <br /> Intensity: Sensitivity
| *Plasmoid | Sine wave based plasma. | Intensity: # of pixels
| *Puddlepeak | Blast coloured puddles randomly up and down the strand with the 'beat'. |Speed: Adjust fade rate.<br /> Intensity: Size of puddles.
| *Puddles | Blast coloured puddles based on volume.| Speed: Fade rate <br /> Intensity: Size of puddle
| *Ripple Peak | Peak detection triggers ripples. | Intensity: Max number of ripples.
| *Waterfall | A volume AND FFT version of a Waterfall.| Speed: Speed <br /> Intensity: Adjust colour
| **2D CenterBars | A 16x16 spectral analysis routine emanating from the center | None.
| **2D DJLight | A 16x16 Matrix like effect using spectrum. | Speed: Speed
| **2D Funky Plank | A 16x16 cool routine.
| **2D GEQ | A 16x16 graphic equalizer.
| **Binmap | Map bins 3-255 throughout the length of the LEDs.<br />Values are not normalized.| Intensity: Max volume 
| **Freqmap | Map the loudest frequency throughout the length of the LED's.| Speed: Fade rate<br /> Intensity: Starting colour 
| **Freqmatrix | See below. | See below
| **Freqpixels | Random pixels coloured by frequency. | Speed: Fade rate<br /> Intensity: Starting colour
| **Freqwave | See below. | See below
| **Gravfreq | VU Meter from center. Log of frequency is index to center colour. | Speed: Speed: Rate of fall<br /> Intensity: Sensitivity
| **Noisemove | Using perlin sound as movement for 3 different frequency bins. |Speed: Speed of perlin movement <br /> Intensity: Fade rate
| **Noisepeak | Blast/fade a single frequency assigned limited palette of perlin noise to the beat (err, really detected peak). | Speed: Adjust fade rate<br /> Intensity: Adjust colour
<br />

## FFT Routines for ESP32 Notes

### Freqmatrix 
The temporal tail for this animation starts at the beginning of the Segment rather than in the center of the segment.

**Sliders used:**
1. Speed: This determines the time delay before each pixel is moved down the line.
1. Intensity: This determines how _MUCH_ the sound input affects the selected effect.

**FFT Sliders:**
1. FFT Low: The low cut off for the FFT bins. Values range from 0-100. Good values are from 0 to 10
1. FFT High: High cut off for the FFT bins. Values range from 0-100. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
1. FFT Custom: This slider works similarly to a **"pre-amp"** for the input signal. The possible values for this slider are 1-10. A good starting point for this is around 2-3.

### Freqwave
This effect maps the major frequencies from the incoming signal to colors in the HSV color space. From the low notes being mapped to red (0) to the high notes being mapped to blue (255) and everything in between. The band you are looking at can be restricted by the FFT Low and FFT High sliders. We are digitizing at 10240Hz, meaning the highest frequency bin that you can find is 5120Hz, which for most music is just fine.
 
**Sliders used:**
1. Speed: This determines the time delay before each pixel is moved down the line.
1. Intensity: This determines how _MUCH_ the sound input affects the selected effect.

**FFT Sliders:**
1. FFT Low: The low cut off for the FFT bins. Values range from 0-100. Good values are from 0 to 10
1. FFT High: High cut off for the FFT bins. Values range from 0-100. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
1. FFT Custom: This slider works similarly to a **"pre-amp"** for the input signal. The possible values for this slider are 1-10. A good starting point for this is around 2-3.


