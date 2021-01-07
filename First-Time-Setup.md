This page is under construction!!!!!!

## Introduction
The sound reactive version of WLED provides all of the functionality of WLED with a few caveats:

* Some of the default services supported by WLED such as Alexa and Blynk are disabled by default.
* Spurious noise and spikes have been problematic during the development of SR WLED. See 'Noise and Spikes' below for further discussion on this topic.
* We recommend using SR WLED in STA mode, instead of the standalone AP mode (aka WLED-AP). It generates more noise.
* If you have problems with the LED's, make sure you can successfully run the latest version of standard WLED.
* Start out with a small strip of ~30 LED's before setting up a large installation.
* Grounding may also be a problem. For example, my line-in setup picked up a lot of noise when my ESP32 board was connected to the USB port on my PC, but NO noise when powered by a USB power bank.
* Connectors!! Dupont connectors are notoriously flaky. I use JST-SM connectors for the LED's and JST-XHP connectors for the microphones.

## First Steps
1. On the WiFi page, it is highly recommended that you connect your SR WLED strip to an existing network.
2. At the bottom of the WiFi page, check on 'Disable WiFi sleep'. May not be necessary if you're not experiencing noise issues.
3. On the LED Preferences page, configure the length of your led strip.
3. On the LED Preference page, configure the 2D matrix size, i.e. 1x30 or 16x16, etc.
4. On the Sound Setting page, set the Squelch setting to '0' and the Gain > 100.
5. On the Effects page, set the animation to '*Gravcenter'.
6. Back on the Sound Settings page, increase/save Squelch setting until strip no longer reacts to the ambient noise.
7. On the Sound Settings page, reduce/adjust the Gain setting until the leds react reasonably with your voice.
8. I also ran pink noise at https://www.youtube.com/watch?v=ZXtimhT-ff4 and fine tuned the values from there.

Here's a starting point table of Squelch and Gain settings for different input types:

| Input | Squelch | Gain
| ----- | ------- | ----
| MAX9814 @40dB | 10 | 10
| Line-In | 1 | 60
| INMP441 | 20 | 5
| ICS-43434 | 20 | 5

Automatic gain control is not currently being used by SR WLED because of so many different input types and ambient settings. We don't know what your 'quiet' is. In addition, the LED's should NOT be reacting when it IS quiet, so it's up to you to make those adjustments. Furthermore, many of the animations can be further adjusted with either the Intensity or Speed slider.

## Noise and Spikes
While providing a lot of functionality, the ESP8266 and the ESP32 boards (typical ones) we have been using have experienced a lot of spurious noise on their ADC pins. This has also been discussed at length on various ESP related forums. Methods to remediate this include:

* Use a separate WiFi antenna.
* Disable the WiFi sleep mode.
* Use shielded wiring for your analog data.
* Use an I2S microphone, such as the INMP441 or ICS-43434.

