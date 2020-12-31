The INMP441 is a high-performance, low power, digital output, omnidirectional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to an ESP32. The recently tested ICS-43434 (thanks to Serg74) also works well.

On an ESP32 (only), if a digital microphone is not detected during startup, Sound Reactive WLED will fall back to analog read.

| INMP441 | Other | ESP32 Pin
| ---- | ---- | ----
| L/R | SEL | Gnd
| SD | DOUT | 32
| WS | LRCL | 15
| SCK | BCLK | 14
| VDD | VDD | 3.3V
| GND | GND | Gnd

Note that 'Other' is supposed to represent the GY-SPH0645 I²S, which did not function correctly during testing with the INMP441 setup.

For an ESP32 in a D1 Mini form factor, you should be able to use GPIO pins 26, 18 and 22. To do so, edit audio_reactive.h, change the pin numbers and then recompile.

Having problems getting the INMP441 running with WLED? Here's a test sketch: https://pastebin.com/Ua7s7LYF

Here's the first board I've seen with the ICS-43434 at: https://www.tindie.com/products/serg74/digital-i2s-microphone-ics-43434-add-on/

I2S support by @spedione