## Introduction

In order to accommodate a wide range of audio inputs, ambient environments and string lengths, we have added user configurable squelch (noise reduction/suppression) and gain controls on the sound settings page that apply to all volume reactive animations.

## Analog Input Pins

We typically recommend using GPIO 36, aka VP or ADC1_CH0 for analog input, however the following pins should also work:

GPIO 32 => ADC1_CH4

GPIO 33 => ADC1_CH5

GPIO 34 => ADC1_CH6

GPIO 35 => ADC1_CH7

GPIO 36 => ADC1_CH0

GPIO 37 => ADC1_CH1

GPIO 38 => ADC1_CH2

GPIO 39 => ADC1_CH3

Do NOT use any of the pins from ADC2, as they will conflict with the WiFi and with I2S sampling.


## Squelch
Adjust this value on the Sound Settings page so that the leds are only activated above a certain 'background noise' level.

## Gain
Line-in signals are typically much lower than that of some of the microphones. Rather than use an auto gain function, you can manually adjust the gain from 1 to 255, which translates to 0.1 up to almost 6.0 gain.

In addition, the 'Intensity' and "input level" sliders can sometimes adjust an animation to simulate increased gain.

## How To
Here's a method to setup squelch and gain for your SR WLED Device.

1. Start out with the routine '*Gravimeter' with default sliders in the middle.
2. Go to the sound settings configuration page.
3. Increase gain to a high value, let's say 234 (or higher) and set the squelch to '1', AGC off, then save.
4. Depending on your input, you should now see the led's flashing, even when the wind blows.
5. In a quiet environment, increase and occasionally save the squelch incrementally until the led's are no longer flashing.
6. Once that's done, make noise appropriate to your 'noisy' environment and number of led's. Then adjust/save the gain so that the led's are responding appropriately.
7. Note that some of the animations allow further sensitivity adjustment with the 'Intensity' setting.
8. Check out the '[Sound Reactive Animations](https://github.com/atuline/WLED/wiki/Reactive-Animations)' page to see what controls are available for each animation.


## Voltage Fluctuation
From faulty microphones to flaky wiring, to WiFi related issues, particularly in AP mode, getting reliable and spike free sound sampling with WLED and in particular analog sampling has been a challenge. Digital microphones such as the INMP441, the ICS-43434 provide the best results.


## Digital Input (I2S)
_to be written_

## AGC - improved Autonomous Gain Control
_to be written_