

***IMPORTANT:*** _Before attempting to compile this fork of WLED, make sure you can compile the [original WLED.](https://github.com/Aircoookie/WLED) If you are unable to compile WLED, please consider flashing your device with [binaries](https://github.com/atuline/WLED/releases/latest) instead._


# Installing pre-built binaries

## Downloading USB Drivers

Download the CH340 drivers at https://www.wemos.cc/en/latest/ch340_driver.html


## Flashing From Binary
The Sound Reactive WLED binaries for ESP32 and Wemos D1 Mini are located [here.](https://github.com/atuline/WLED/releases)

<br/>

### unofficial development binaries - here be dragons
You can find some unofficial SR WLED binaries, including intermediate development builds for ESP32, here:

Installation services
* https://wled-install.github.io
* https://install.wled.me

Firmware Binaries
* https://github.com/srg74/WLED-wemos-shield/tree/master/resources/Firmware/Sound_reactive 
* https://github.com/wled-install/wled-install.github.io


Please keep in mind that these sites are not maintained by the SR WLED team. 
You may find old outdated binaries, or binaries that might not work on generic ESP32 hardware. So please compare build number and dates, and read descriptions before installing one of these.


### Flashing ESP32 Binaries with esptool

_Warning_: We had to change the partition size on the ESP32 in order to 'fit' all the new features. This means that the 'old way' of upgrading/flashing, no longer work unfortunately. **You cannot use ESPHome Flasher**, and you cannot use OTA from a build prior to b5.

1. Download [esptool](https://github.com/espressif/esptool).
1. Download the ESP32 bootloader, such as https://github.com/Aircoookie/WLED/releases/download/v0.13.1/esp32_bootloader_v4.bin
1. Download the sound reactive binary, such as https://github.com/atuline/WLED/releases
1. Plug the ESP32 board into your computer.
1. Optionally determine which Com port it uses. You could use NodeMCU-PyFlasher to do this, but don't flash the binary with it.
1. Open a Command prompt on your computer.
1. Assuming you copied esptool and both binaries to the same directory, you could clear the contents of the ESP32 with:

    ` esptool.exe erase_flash`
1. Then burn the bootloader with:

    `esptool.exe write_flash 0x0 esp32_bootloader_v4.bin`
1. Once complete, you can now burn the sound reactive binary with:

    `esptool write_flash 0x10000 soundReactive_WLED_0.13.X-bY_ESP32dev.bin`

1. You can optionally add the port, such as '-p COM6'.
1. In addition, if this is the first time you've used this version, you need to go to the "Security & Updates" settings page and tick the "Factory reset" box, then select "Save & Reboot". Caveat: May not be necessary if you ran 'erase_flash' above.
1. This will reset the EEPROM and remove any settings or presets you may have saved.

Note: If you Flash via another method, you will definitely need to perform a Factory Reset. Cycling the power is also a requirement if you're doing anything with I2S.


### Flashing ESP8266 Binaries

1.  Download for your platform [NodeMCU-PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases).
1.  Plug the WeMOS D1 Mini (or other ESP8266 device) into your computer.
1.  Run NodeMCU-PyFlasher.
1.  Load the binary.
1.  Select the Com port.
1.  Select 'yes, wipes all data'.
1.  Press Flash NodeMCU.


# Compiling from Platform IO

### Getting started

<b>&rAarr; first read https://kno.wled.ge/advanced/compiling-wled/ </b> <br/>
  &rarr; source code from https://github.com/atuline/WLED/tree/master<br/>
  &rarr; start with one of the sound reactive compile environments, like  [`env:soundReactive_esp32dev`](https://github.com/atuline/WLED/blob/3752b78d3b845f722ba043d92007cc79aa811561/platformio.ini#L444)<br/>
  &rarr; read wled00/config.h, add your own settings to wled00/my_config.h <br/>
  &rarr; create your own compile environment(s) using platformio_override.ini

SoundReactive has some additional compile time options - see [`wled00/audio_reactive.h`](https://github.com/atuline/WLED/blob/master/wled00/audio_reactive.h#L27) and [`wled00/audio_source.h`](https://github.com/atuline/WLED/blob/3752b78d3b845f722ba043d92007cc79aa811561/wled00/audio_source.h#L20).

### Additional compile guidelines
* If you get .py errors, install Python (wait for the VSCode popup to install Python)
* If you do not install the Arduino IDE (Why should you if you have PlatformIO) and your board is not recognised if you compile to board, install the [USB to UART bridge VSP Drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)
* For the sound reactive ESP32 firmware, the board type should be env:soundreactive_esp32dev. This is because we have modified the build partitions in order to go beyond the original compile size limits of WLED.


Note: We have long since stopped compiling WLED with the Arduino IDE.
