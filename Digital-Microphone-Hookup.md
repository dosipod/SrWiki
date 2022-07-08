The INMP441 is a high-performance, low power, digital output, omnidirectional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to an ESP32 (but NOT an ESP8266). The recently tested ICS-43434 (thanks to Serg74) also works well.

<br/>

| INMP441 | Other | ESP32 Pin | ESP32 D1 Mini
| ---- | ---- | ---- | ----
| L/R | SEL | Gnd | Gnd
| SD | DOUT | 32 | 16
| WS | LRCL | 15 | 22
| SCK | BCLK | 14 | 18
| VDD | VDD | 3.3V | 3.3V
| GND | GND | Gnd | Gnd

**Important**: please make sure that your I2S device provides sound input on the **LEFT audio channel**! For the INMP441 this is achieved by wiring the 'L/R' connection to GND (ground).

<br/>

Since 0.12.0, you can change I2S pins in the [Sound Settings](https://github.com/atuline/WLED/wiki/Sound-Settings) interface; on ESP32 any available GPIO can be used for I²S. The 'SD' signal can also be mapped to an input-only (GPI) pin. You'll need to reboot when done with pin assignment - don't forget to "save". To reboot, please press 'reset' on your ESP32. Unfortunately a restart by software ("soft reboot") is not always sufficient to activate new driver settings.


In older releases, you need to change pins used by defining `I2S_WS`, `I2S_SD`, and `I2S_SCK` in your PlatformIO config, or by editing the values in audio_reactive.h. 

Note that 'Other' is supposed to represent the GY-SPH0645 I²S, which did not function correctly in older releases of WLED-SR when testing with the INMP441 setup.

We do not have these digital microphones running on an ESP8266.

In addition to I2S microphones, there are solutions availeable for line-in via I2S. We already have driver support for Boards/Shields with "es7243" chip, and we're investigating "es8388". 

In addition, other I2S ADC (analog-to-digital-converter) devices and microphones that have a [standard I2S interface](https://en.m.wikipedia.org/wiki/I%C2%B2S) may already work with WLED-SR, by using one of the "Generic I2S" drivers (`Generic I2S`, `Generic I2S PDM`, or `Generic I2S with Mclk`). It is important however that sound input is availeable on the **LEFT audio channel**. Please keep in mind that WLED-SR is a spare-time open source project - we do our best to make generic drivers but we cannot test with all available devices.

Having problems getting the INMP441 running with WLED? Here's a test sketch (which you can compile with the Arduino IDE): https://pastebin.com/Ua7s7LYF
. If you are still having a problem with that sketch, change the line with ONLY_LEFT to ONLY_RIGHT. If that works, you'll need to go into audio_source.h and change that line.

Here's the first board I've seen with the ICS-43434 at: https://www.tindie.com/products/serg74/digital-i2s-microphone-ics-43434-add-on/

Looking to add line-in with I2S support? Try https://www.akm.com/content/dam/documents/products/audio/audio-adc/ak5720vt/ak5720vt-en-datasheet.pdf

I2S support by @spedione