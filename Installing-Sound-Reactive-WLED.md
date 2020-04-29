Before attempting to compile this fork of WLED, make sure you CAN compile the one from [wled.me](http://wled.me).

If you are unable to compile WLED, please consider flashing your device with binaries instead.


## Flashing from binary

The following instructions show you how to flash the original (not sound reactive) WLED binary to a WeMOS D1 Mini. 

See: https://www.youtube.com/watch?v=4EXefD6INos

1.  The sound reactive binaries are located here: https://github.com/atuline/WLED/releases
1.  For sound-reactive WeMOS D1 Mini, download and save WLED_0.9.1_ESP8266_Sound.bin
1.  The original WLED binaries are located here: https://github.com/Aircoookie/WLED/releases
1.  Download [NodeMCU-PyFlasher Latest](https://github.com/marcelstoer/nodemcu-pyflasher/releases) which works on Windows and macOS
1.  Plug the WeMOS D1 Mini into your computer
1.  Run NodeMCU-PyFlasher
1.  Load the binary
1.  Select 'yes, wipes all data'
1.  Press Flash NodeMCU

The sound reactive WLED binary is located as follows:
*   ESP8266 binary: https://github.com/atuline/WLED/releases/download/v0.9.1-s1/WLED_0.9.1_ESP8266_Sound.bin
*   ESP32 binary: <not yet available>


## Compiling from a fresh install of the Arduino IDE

1. Download and install the Arduino IDE from [arduino.cc](https://www.arduino.cc/en/Main/Software). Defaults are OK.
1. Start the Arduino IDE and add ESP8266/ESP32 board support by going to "File | Preferences" ("Arduino | Preferences" for macOS (⌘,))
1. In the "Additional Boards Manager URLs" section, copy these URL's and add: https://arduino.esp8266.com/stable/package_esp8266com_index.json for an ESP8266 and https://dl.espressif.com/dl/package_esp32_index.json for an ESP32. You can add both by separating them with a comma. 
1. Press "OK" to install support for the ESP8266/ESP32 platform
1. Go to "Tools | Board | Boards Manager..."
1. For the ESP8266/32, search for "ESP8266" and/or "ESP32"
1. Click on "Install" for each.
1. As of April 2020, the current version for ESP8266 was 2.6.3
1. As of April 2020, the current version for ESP32 was 1.0.4

If you already have ESP8266/32 drivers installed, please ensure your drivers are recent:

1. Go to "Tools | Board | Boards Manager...".
1. For the ESP8266/32, search for "ESP8266" or "ESP32"
1. As of April 2020, the current version was 2.6.3
1. As of April 2020, the current version was 1.0.4


**Note:** Before attempting to compile WLED, make sure you can select your ESP board and compile a basic sketch such as:
"File | Examples | 01.Basics | Blink"


## WLED library pre-requisites:

WLED makes use of a LOT of 3rd party libraries and is NOT easy to compile, especially for anyone new to Arduino. Although the WLED distribution contains several of these libraries, it doesn't include them all. Additional libraries you need to install are:

* NeoPixelBus by Makuna
* FastLED
* IRRemoteESP8266 (ESP8266 Only)
* ArduinoFFT (ESP32 Only)
* ESPAsyncTCP (ESP8266 Only)
* ESPAsyncUDP (ESP8266 Only)
* ESPAsyncWebServer
* AsyncTCP (ESP32 Only)


See the next section to find/install these libraries.

## Install libraries that are included in the Library Manager

1. Navigate to "Tools | Manage Libraries..." or "Sketch | Include Libraries | Manage Libraries..." for macOS (⇧⌘I)
1. Search for and install "NeoPixelBus by Makuna"
1. Search for and install "FastLED by Daniel Garcia"
1. Search for and install "IRremoteESP8266 by Ken Shirriff, etc"
1. Search for and install "arduinoFFT by Enqrique Condes"

## Install libraries that are not included in the Library Manager:

To install libraries that are not in the library manager, you would typically:

1. Download the zip file
1. In the Arduino IDE use "Sketch | Include Library | Add Zip Library"
1. Navigate to where you downloaded the .zipped library.
1. Select it and press OK.
1. Your library should now be included if you go "Sketch | Include Libraries" and navigate down to Contributed libraries.

1. Download and install [ESPAsyncTCP](https://github.com/me-no-dev/ESPAsyncTCP)
1. Download and install [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer)
1. Download and install [ESPAsyncUDP](https://github.com/me-no-dev/ESPAsyncUDP)
1. For ESP32 Download and install [AsyncTCP](https://github.com/me-no-dev/AsyncTCP)

If you add the library manually or with git you will most likely need to **restart**, yes **restart** the Arduino IDE before it will be recognized. For more information on libraries, see: https://www.arduino.cc/en/Guide/Libraries.

### Download WLED
* In a web browser you can navigate to wled at [wled.me](https://github.com/Aircoookie/WLED) and unzip into a new directory.
* You can then 'Download' the Zip file.
* Unzip it into a new directory.
* If you have 'git' installed, in an appropriate directory, you can run:
`"git clone https://github.com/Aircookie/WLED.git WLED"`

### Compiling WLED

Once you have:

* Installed Arduino IDE.
* Installed support for ESP32/ESP8266.
* Updated the drivers on an existing installation of the IDE.
* Downloaded and installed the library pre-requisites.
* Downloaded and installed WLED.

You should now be able to compile and upload WLED to your ESP device.

If this feels like a treasure hunt, it is. Now, imagine what the authors of WLED had to go through just
to get this all working together. We just figured out how to compile it and to get some sound reactive code running.
