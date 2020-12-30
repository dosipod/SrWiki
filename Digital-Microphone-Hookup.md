The INMP441 is a high-performance, low power, digital output, omnidirectional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to an ESP32. The recently tested ICS-43434 also works well, however we're not available of any mass produced boards for that microphone (as of Dec 2020).

On an ESP32 (only), if an INMP441 is not detected during startup, Sound Reactive WLED will fall back to analog read.

| INMP441 | Other | ESP32 Pin
| ---- | ---- | ----
| L/R | SEL | Gnd
| SD | DOUT | 32
| WS | LRCL | 15
| SCK | BCLK | 14
| VDD | VDD | 3.3V
| GND | GND | Gnd

Note that 'Other' is supposed to represent the GY-SPH0645 I²S, which did not function correctly during testing with the INMP441 setup.

Having problems getting the INMP441 running with WLED? Here's a test sketch: https://pastebin.com/Ua7s7LYF

Here's the first board I've seen with the ICS-43434 at https://www.tindie.com/products/serg74/digital-i2s-microphone-ics-43434-add-on/

INMP441 support by @spedione