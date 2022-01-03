***IMPORTANT:*** _Before attempting to compile this fork of WLED, make sure you can compile the [original WLED.](https://github.com/Aircoookie/WLED) If you are unable to compile WLED, please consider flashing your device with [binaries](https://github.com/atuline/WLED/releases/latest) instead._

## Downloading USB Drivers

Download the CH340 drivers at https://www.wemos.cc/en/latest/ch340_driver.html


## Flashing From Binary
The Sound Reactive WLED binaries for ESP32 and Wemos D1 Mini are located [here.](https://github.com/atuline/WLED/releases/latest)

### Flashing ESP8266 Binaries

1.  Download for your plateform [NodeMCU-PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases).
1.  Plug the WeMOS D1 Mini (or other ESP8266 device) into your computer.
1.  Run NodeMCU-PyFlasher.
1.  Load the binary.
1.  Select the Com port.
1.  Select 'yes, wipes all data'
1.  Press Flash NodeMCU

### Flashing ESP32 Binaries

1. Download [esptool](https://github.com/espressif/esptool).
1. Download the ESP32 bootloader, such as https://github.com/Aircoookie/WLED/releases/download/v0.13.0-b5/esp32_bootloader_v4.bin
1. Download the sound reactive binary, such as https://github.com/atuline/WLED/releases/download/v0.13.0-b4/soundReactive_WLED_0.13.0-b4_ESP32.bin
1. Plug the ESP32 board into your computer.
1. Determine which Com port it uses. You could use NodeMCU-PyFlasher to do this, but don't flash the binary with it.
1. Open a Command prompt on your computer.
1. Assuming you copied esptool and both binaries to the same directory, you could burn the bootloader with:
1. esptool.exe write_flash 0x0 esp32_bootloader_v4.bin
1. Once complete, you can now burn the sound reactive binary with (the -p COM6 is optional):
1. esptool.exe -p COM6 write_flash 0x010000 soundReactive_WLED_0.13.0-b4_ESP32.bin


**NOTE:** If you are flashing a newer version, or if you have issues after installing the binary, please go to the "Security & Updates" settings page and tick the "Factory reset" box, then select "Save & Reboot". This will reset the EEPROM and remove any settings or presets you may have saved.



## Compiling from Platform IO

Note: We have long since stopped compiling WLED with the Arduino IDE.

https://github.com/Aircoookie/WLED/wiki/Compiling-WLED

Additional compile guidelines
* If you get .py errors, install Python (wait for the VSCode popup to install Python)
* If you do not install the Arduino IDE (Why should you if you have PlatformIO) and your board is not recognised if you compile to board, install the [USB to UART bridge VSP Drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)
* For the sound reactive ESP32 firmware, the board type should be env:soundreactive_esp32dev. This is because we have modified the build partitions in order to go beyond the original compile size limits of WLED.
