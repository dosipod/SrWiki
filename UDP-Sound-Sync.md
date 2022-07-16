UDP Sound Sync is a feature to synchronize (share) the sound input of a 'master' device with one or more 'slave' devices. All devices must be running the same release of SR WLED, and they must be in the same network. Sound Sync is not availeable in "upstream" WLED by Aircookie. Sound Sync is also different from direct LEDs control using protocols like E1.31, DMX, or AdaLight.

UDP Sound Sync does not sync the actual animations, but rather transmits summary audio sampling information to several devices that still run their own animations locally. In a nutshell, it means that several devices can share a single microphone.

## Setup
Before configuring UDP Sound Sync, make sure you have gone into the WiFi Preferences and clicked on 'Disable WiFi sleep' at the bottom of the page. It has caused us innumerable problems in the past.

In order to configure UDP sound sync, the ‘master’ needs to be an ESP32 along with an [audio input](https://github.com/atuline/WLED/wiki/Sound-Settings).

You would then to go the ‘Sync Interfaces’ page and configure the 'Audio Sync' at the bottom of the page. `Transmit` for the ESP32 and `Receive` for devices without an audio input (either ESP32's or ESP8266's). Make sure the UDP port is the same on all devices.

This does not sync the actual animations, but rather just the transmission of summary audio sampling information (as best we can).

In order to change the UDP Sync Mode (Disabled/Transmit/Receive), you need to power-cycle the ESP32/ESP8266.

## Technical

When an ESP32 is configured for audio transmission, it will connect to a UDP Multicast address, and begin sending a single UDP Multicast packet containing the data used to generate sound-reactive animations out to any other devices that are configured to receive on the same network.  The following information is transmitted:
```
  char header[6] = UDP_SYNC_HEADER;
  uint8_t myVals[32];     //  32 Bytes
  int sampleAgc;          //  04 Bytes
  int sample;             //  04 Bytes
  float sampleAvg;        //  04 Bytes
  bool samplePeak;        //  01 Bytes
  uint8_t fftResult[16];   // 16 Bytes
  double FFT_Magnitude;   //  08 Bytes
  double FFT_MajorPeak;   //  08 Bytes
```

UDP_SYNC_HEADER is a versioning number that's defined in audio_reactive.h

## What else ?

When an ESP32 or ESP8266 is configured to receive audio data from another device, the receiver will disable any onboard microphone sampling and FFT processing, in favor of audio data received from the network.  Any time a UDP Multicast packet is received from a transmitter, it will be treated as a discrete microphone sample and stored in memory the same way it would be if it were a local microphone.

* An ESP8266 will not be able to use any FFT data transmitted from an ESP32, as a result of the differences in hardware and software.

* The default UDP Multicast IP is 239.0.0.1, and the default port is 11988.

* UDP multicast is generally not very reliable with typical "consumer grade hardware". Some user found that creating a "port forwarding rule" on their local Wifi router helps. For example, you could create a "dynamic port forwarding rule" for UDP port 11988.


UDP Sound sync brought to you by @spedione on Discord.

Reference: https://github.com/Aircoookie/WLED/wiki/UDP-Realtime-Control


