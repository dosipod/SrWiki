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

<br/>

Since 0.12.0, you can change the pins in the [Sound Settings](https://github.com/atuline/WLED/wiki/Sound-Settings) interface; on ESP32 any available GPIO can be assigned to I²S. The 'SD' signal can also be mapped to an input-only (GPI) pin. You'll need to reboot when done with pin assignment. 

In older releases, you need to change pins used by defining `I2S_WS`, `I2S_SD`, and `I2S_SCK` in your PlatformIO config, or by editing the values in audio_reactive.h. 

Note that 'Other' is supposed to represent the GY-SPH0645 I²S, which did not function correctly in older releases of WLED-SR when testing with the INMP441 setup.

We do not have these digital microphones running on an ESP8266.

Having problems getting the INMP441 running with WLED? Here's a test sketch (which you can compile with the Arduino IDE): https://pastebin.com/Ua7s7LYF
. If you are still having a problem with that sketch, change the line with ONLY_LEFT to ONLY_RIGHT. If that works, you'll need to go into audio_source.h and change that line.

Here's the first board I've seen with the ICS-43434 at: https://www.tindie.com/products/serg74/digital-i2s-microphone-ics-43434-add-on/

Looking to add line-in with I2S support? Try https://www.akm.com/content/dam/documents/products/audio/audio-adc/ak5720vt/ak5720vt-en-datasheet.pdf

I2S support by @spedione