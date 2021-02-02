During the development of our sound reactive version of WLED, we've had several challenges with WiFi along with the ADC capability of the ESP devices.

###ESP8266

After the conversion to .cpp files, our ESP8266 code lost connection between the user interface and the ESP8266's web server. This eventually culimated in re-writing a stripped down version of SR WLED dedicated just for the ESP8266. It included the UDP sound sync as a receiver, but supported none of the FFT or 2D functionality. This stripped down version seems to be stable, however that platform is now deprecated from further development.

###ESP32

