THIS IS STILL A WORK IN PROGRESS
My plan on the software/firmware side of things is to use this structure:

Surface laptop running QGround Control with video feed going to Oculus via USB C
(Q ground control sends the signals from the PS4 controller down and allows me to stream the cameras from my computer into the VR headset)

^^^^^

MavLink communication protocol through ethernet tether

^^^^^^

Rasberry pi companion computer running BlueOS
(BlueOS Allows the Rasberry Pi to talk to the pixhawk and the surface computer through the tether and Mavlink) 

^^^^^

Pixhawk running ArduSub
(ArduSub turns the signals coming out of the rasberry pi into PWM controls going to each of the 6 motor's ESCs based on the thrust mapping (which I have yet to do) and it recieves I2C signals from the pressure sensor/power module to send that back up)

^^^^^^^

Motors flashed with BLHeli_S allowing them to spin backwards on command.

[Here is the link to the sourcecode for ArduSub](https://github.com/ArduPilot/ardupilot/tree/master/ArduSub?utm_source=chatgpt.com)

[Here is the link to the sourcecode for BLHeli_S](https://github.com/bitdump/BLHeli/tree/master/BLHeli_S%20SiLabs?utm_source=chatgpt.com)

[Here is the link to the sourcecode for BlueOS](https://github.com/bluerobotics/BlueOS?utm_source=chatgpt.com)

[Here is the sourcecode for QGroundControl](https://github.com/mavlink/qgroundcontrol?utm_source=chatgpt.com)
