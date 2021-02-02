During the development of our sound reactive version of WLED, we've had several challenges with WiFi along with the ADC capability of the ESP devices.


### ESP8266

After the conversion to .cpp files, our ESP8266 code lost connection between the user interface and the ESP8266's web server. This eventually culimated in re-writing a stripped down version of SR WLED dedicated just for the ESP8266. It included the UDP sound sync as a receiver, but supported none of the FFT or 2D functionality. This stripped down version seems to be stable, however that platform is now deprecated from further development.


### ESP32

Although the ESP32 did lose connection with the web server, it was nowhere near as bad as the ESP8266. 


### Both platforms

On both platforms, we encountered significant spikes when using the analog ADC when the WiFi is active. There are numerous articles on this issue, along with various methods to reduce the noise. We've found that an I2S microphone, such as the INMP441 or ICS-43434 will provide a better response than any of the analog microphones or input methods that we support.

