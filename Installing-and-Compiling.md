***IMPORTANT:*** _Before attempting to compile this fork of WLED, make sure you can compile the [original WLED.](https://github.com/Aircoookie/WLED) If you are unable to compile WLED, please consider flashing your device with [binaries](https://github.com/atuline/WLED/releases/latest) instead._


## Flashing From Binary



The following instructions show you how to flash the original (not sound reactive) WLED binary to a WeMOS D1 Mini. 

See: https://www.youtube.com/watch?v=4EXefD6INos

1.  The Sound Reactive WLED binaries for ESP32 and Wemos D1 Mini are located [here.](https://github.com/atuline/WLED/releases/latest)
1.  The Original WLED binaries are located [here.](https://github.com/Aircoookie/WLED/releases/latest)
1.  For the ESP32, you can download the [ESP Home Flasher](https://github.com/esphome/esphome-flasher/releases/latest). For some reason, the NodMCU Pyflasher hasn't been working on this platform for a while.
1.  Download [NodeMCU-PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases) or [esptool.py](https://github.com/espressif/esptool) which works on Windows and macOS
    1. **NOTE:** For ESP32 you must write flash at 0x10000 and program the bootloader. There are great [instructions here](https://github.com/Aircoookie/WLED/wiki/Install-WLED-binary).
1.  Plug the WeMOS D1 Mini into your computer
1.  Run NodeMCU-PyFlasher
1.  Load the binary
1.  Select 'yes, wipes all data'
1.  Press Flash NodeMCU
1. **NOTE:** If you are flashing a newer version, or if you have issues after installing the binary, please go to the "Security & Updates" settings page and tick the "Factory reset" box, then select "Save & Reboot". This will reset the EEPROM and remove any settings or presets you may have saved.

## Compiling from Platform IO

https://github.com/Aircoookie/WLED/wiki/Compiling-WLED

Additional compile guidelines
* If you get .py errors, install Python (wait for the VSCode popup to install Python)
* If you do not install the Arduino IDE (Why should you if you have PlatformIO) and your board is not recognised if you compile to board, install the [USB to UART bridge VSP Drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)

## Compiling from a fresh install of the Arduino IDE

https://github.com/atuline/WLED/wiki/Arduino-IDE-Compile-(Outdated)
