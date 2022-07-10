# soyo-control
control SOYO grid-tie solar inverters with ESP microcontrollers

To control the Soyo 1000W/1200W Grid-Tie inverter over RS485, there are different projects here on GitHub:
Unfortunately only closed source:
https://github.com/KlausLi/Esp-Soyosource-Controller

Some Phython Sources and measurements
https://www.photovoltaikforum.com/thread/148552-g%C3%BCnstiger-1200w-grid-tie-inverter-mit-limiter-sensor-von-soyo-source-%C3%A4hnlich-gti/?postID=2551586#post2551586

Python Sources for the Raspberry Pi
https://github.com/drcross/virtualmeter

# My approach
A Shelly 3EM Power meter sends the current power measurements to my MQTT broker. The ESP is placed close to the Soyo inverter and receives the measurements. The ESP calulates the Power the Soyo should deliver.
