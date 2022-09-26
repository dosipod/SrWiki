The INMP441 is a high-performance, low power, digital output, omni-directional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to an ESP32 (but NOT an ESP8266). The recently tested ICS-43434 (thanks to Serg74) also works well, and just requires a slightly higher squelch setting (~10).

<br/>

| INMP441 <br/> and ICS-43434 | Other<br/>incl. SPH0645 | ESP32 GPIO | ESP32 D1 Mini GPIO | |
| ---- | ---- | ---- | ---- | --- |
| L/R | SEL | Gnd | Gnd | ground => left channel
| SD | DOUT | 32 | 16 | serial data
| WS | LRCL | 15 | 22 | left right clock
| SCK | BCLK | 14 | 18 | serial clock
| VDD | VDD | 3.3V | 3.3V | power don't use 5V!
| GND | GND | Gnd | Gnd | ground, 0V

**Important**: please make sure that your I2S device provides sound input on the **LEFT audio channel**! For the INMP441 this is achieved by wiring the 'L/R' connection to GND (ground). Only exception is the "ES7243" driver, which is always using the _RIGHT_ audio channel.

<br/>

Since 0.12.0, you can change I2S GPIO pins in the [Sound Settings](https://github.com/atuline/WLED/wiki/Sound-Settings) interface; on ESP32 any available GPIO can be used for I²S. The 'SD' signal could also be mapped to an input-only (GPI) pin _(*)_, if you are low on GPIO pins. You'll need to reboot when done with pin assignment - don't forget to "save". To reboot, please press 'reset' on your ESP32. Unfortunately a restart by software ("soft reboot") is not always sufficient to activate new driver settings.

**Important:** _(*)_ Due to a problem that was fixed very recently, its not possible to use input-only GPI pins in older releases of SR WLED. There will be no warning if you try to do so. This problem is solved in the [latest release version of SR WLED](https://github.com/atuline/WLED/releases).


In older releases, you need to change pins used by defining `I2S_WS`, `I2S_SD`, and `I2S_SCK` in your PlatformIO config, or by editing the values in audio_reactive.h. 

In addition to I2S microphones, there are solutions available for line-in via I2S. We already have driver support for Boards/Shields with "es7243" chip, and we're investigating "es8388". 

Other I2S ADC (analog-to-digital-converter) devices and microphones that have a [standard I2S interface](https://en.m.wikipedia.org/wiki/I%C2%B2S) may already work with WLED-SR, by using one of the I2S "Generic" drivers (`Generic I2S`, `Generic I2S PDM`, or `Generic I2S with Mclk`). It is important however that sound input comes on the **LEFT audio channel**. Please keep in mind that this is a spare-time open source project - we do our best to make generic drivers but we cannot test with all available devices.

We do not have these digital microphones running on an ESP8266.

Having problems getting the INMP441 running with WLED? Here's a test sketch (which you can compile with the Arduino IDE): https://pastebin.com/Ua7s7LYF
. If you are still having a problem with that sketch, change the line with ONLY_LEFT to ONLY_RIGHT. If that works, you'll need to go into audio_source.h and change that line.

Initial I2S support by @spedione

<hr/>

## Some I2S audio boards

Here's the first board I've seen with the ICS-43434 at: https://www.tindie.com/products/serg74/digital-i2s-microphone-ics-43434-add-on/

Looking to add line-in with I2S support? Try https://www.akm.com/content/dam/documents/products/audio/audio-adc/ak5720vt/ak5720vt-en-datasheet.pdf


ES7243 based boards:
* [ESP32 Lyra-T mini](https://docs.espressif.com/projects/esp-adf/en/latest/design-guide/dev-boards/board-esp32-lyrat-mini-v1.2.html#esp32-lyrat-mini-v1-2-hardware-reference)

ES8388 based boards, with I2S on-board microphone and I2S Line-In (**SR WLED support not available yet**, but being devoloped)
* [ESP32 Lyra-T](https://docs.espressif.com/projects/esp-adf/en/latest/design-guide/dev-boards/board-esp32-lyrat-v4.3.html)
* [Ai-Thinker ESP32 Audio Kit](https://docs.ai-thinker.com/en/esp32-audio-kit)

See also https://github.com/atuline/WLED/issues/118.
