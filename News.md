What's possibly on the horizon (no dates given):

* Cleaning up volume acquisition routines to just get volume from FFT_Magnitude.
* Modify both analog and digital data acquisition to read I2S in blocks.
* Some folks are interested in higher sampling rates. We may look for outside work on that.
* Possibly improved 2D support.
* Smoothing.
* Some more animations.

### January 13, 2021

* Well that was a year, only for 2021 to say 'hold my beer'.
* We've been working on fixing bugs, including UDP sync issues among others.
* Normalizing frequency and volume response for different microphones.
* Testing/updating various routines to work with the above changes.
* Modified routines to better support the 'FastLED' way of doing things, specifically for leds[i+1] = leds[i] and vice versa.
* Dealing with platform related noise and spikes. Had to add an exponential filter combined with the squelch control.
* Added a few more animations, and took out one or two.


### November 5, 2020

* The ESP8266 branch continues to be reliable for that platform, but NOT reliable for the regular build. Would love to know why.
* Have fixed issues around SEGMENTS for various sound reactive animations. Ths issue was SEGMENT specific 'persistent' variables. Use the uint16_t SEGENV.aux0 or SEGENV.aux1 variables if you need those.
* That was updated for both the dev and ESP8266 branches.
* We now have a dedicated Sound Settings page.


### August 22, 2020

* Our dev build now has INMP441 (digital microphone) support for the ESP32.
* Our dev build also now has a Gain settings control for volume reactive or '*' routines.
* Neither update has been rolled up into our main branch.
* We've had a lot of issues with AP mode and ESP8266's, so Andrew created an ESP8266 branch, downloaded the latest version of WLED and added just the volume reactive functionality to that branch.
* We'll be removing ESP8266 support from our dev and main branches over time. That will simplify coding significantly.
* apleschu is still busy with his cross continental move.
