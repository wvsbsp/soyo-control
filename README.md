# soyo-control
control SOYO grid-tie solar inverters with ESP microcontrollers

To control the Soyo 1000W/1200W Grid-Tie inverter over RS485, there are different projects here on GitHub:
Unfortunately the only one for the ESP is closed source:
https://github.com/KlausLi/Esp-Soyosource-Controller

Some Phython Sources and measurements
https://www.photovoltaikforum.com/thread/148552-g%C3%BCnstiger-1200w-grid-tie-inverter-mit-limiter-sensor-von-soyo-source-%C3%A4hnlich-gti/?postID=2551586#post2551586

Python Sources for the Raspberry Pi
https://github.com/drcross/virtualmeter

# My approach
A Shelly 3EM Power meter sends the current power measurements to my MQTT broker. The ESP is placed close to the Soyo inverter and receives the measurements. The ESP calulates the Power the Soyo should deliver.

# Hardware
You can use any ESP8266 or ESP32. 
- The ESP8266 has only one serial port, that is needed to program the device or read messages over the serial monitor. Here we have to use SoftwareSerial.h to create a second serial port.
- The ESP32 has more than one serial port, so i will use Serial2 on Pins GPIO16 (RxD2) and GPIO17 (TxD2). The RS-485 driver is connected to these pins. For universal use, i connect the receive enable /RE and transmit enable DE _not_ to one but two pins. So you can enable receiving while transmitting and check that your values appear correctly on the RS-485 bus.
- Use an RS-485 driver, that works with 3.3V Vcc, such as the MAX3485. Do not use voltage dividers in the RxD-line (which will work at the slow speeds but might kick back in the future)
- You can add a display and some buttons to the ESP to change settings (or start an accesspoint on the ESP for that purpose). I use a 0.96" OLED display with I2C bus and 128x64 pixels. (now the ESP8266 is pretty much full...)
