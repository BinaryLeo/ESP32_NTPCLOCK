# ESP32_NTPCLOCK
Heltec ESP32 RTC - NTP Server 


![photo_2021-10-18_00-36-26](https://user-images.githubusercontent.com/72607039/137672384-09297191-34c0-4c7a-b5a8-ce79c590750d.jpg)


"Heltec WiFi Kit 32 NTP Clock" is a ntp initialized date and time clock. 
The device connects to the an ntp time server via wifi and a udp port, obtains the ntp time from the server, adjusts then writes
the time to the ESP32 rtc (real time clock), and displays the date and time on the built in OLED display.

Upon startup, the code initializes the serial port, wifi, graphics and udp port.  The serial port is used only during initialization to display when the wifi is connected and when the ntp time has been received from the ntp server.  
Wifi is used to communicate with the ntp server.  The graphics is used to display the initialization and operational displays on the built in OLED.  Finally, the udp port receives the ntp time from the ntp server.

![heltec2](https://user-images.githubusercontent.com/72607039/137674802-38433452-5c77-4d39-966e-9c793261293f.jpg)


The main loop performs two major functions; obtains the time from the ntp server and to update the oled.
In this example, the time is obtained from the ntp server only once, and upon receipt, is adjusted for time zone then written into the ESP32 rtc (real time clock).
The OLED is updated once per pass, and there is a 200ms delay in the main loop so the OLED is updated 5 times a second.

Before compiling and downloading the code, adjust the following settings:
1) TIME_ZONE  - currently set to -3 for Brazil (My home state), adjust to your timezone.
2) chPassword - currently set to "YourWifiPassword", adjust to your wifi password.
3) chSSID     - currently set to "YourWifiSsid", adjust to your wifi ssid.


![heltec](https://user-images.githubusercontent.com/72607039/137672252-1cd1f805-63fc-47e1-98c5-f1d9968d2539.jpg)


Setup Your Heltec board:
https://heltec-automation-docs.readthedocs.io/en/latest/esp32/quick_start.html

U8g2 library:
https://github.com/olikraus/u8g2/wiki