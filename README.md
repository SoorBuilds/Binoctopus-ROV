<img width="1728" height="1117" alt="Screenshot 2026-09-12 at 11 26 09 PM" src="https://github.com/user-attachments/assets/e0508038-605a-43c6-8036-1035a92e72b1" />

# Binoctopus-ROV

A stereoscopic underwater FPV drone

If you have ever wanted to explore the underwater world without getting wet, you can understand my motivation for designing this! I love the water and pretending to be a fish, but due to an ear problem I cant dive any deeper than 2m underwater :(
I knew I wanted to make an underwater drone to combat this issue, but none of the tutorials I could find online looked any good. They just WEREN'T IMMERSIVE! I set out to design a low budget, yet extremely immersive ROV and this design is my result so far. I expect it will need further iteration, but so far, My idea is to take two gopros and use them in webcam mode to stream 1080p60fps low latency up to the surface through a companion computer rasberry pi. Here is an image of the housing I designed for the gopros to be encased in an acrylic pipe with a custom 3d printed encap potted with epoxy for hypothetical pressure resistance up to 8.5 bar (85m underwater): 
<img width="1728" height="1117" alt="Screenshot 2026-09-13 at 12 14 38 AM" src="https://github.com/user-attachments/assets/2013f0d5-9e91-4ec7-8aa6-a7f096849d6c" />
But hold on... Why have two? 
After a ton of research into the cheapest way to get the best immersion on a tight budget, I discovered the Stereoscopic FPV community. FPV flying drone enthusiasts swear by a dual camera approach so that you can get depth perception, the same way that your two eyes do. By streaming the feed from one camera into one of the screens on a VR headset, and the right into the right for example, you would end up with a VERY natural feeling viewing experience, almost like looking through your own eyes.
Image of my oculus quest VR heasdet I will use to view the stereo video feeds:
<img width="2181" height="1636" alt="IMG_9706" src="https://github.com/user-attachments/assets/59e52620-ba69-49b8-b7c6-5a9cdeb2454a" />

Of course, this stereo vision needs to be paired with High resolution and low latency, both of which are usually very costly.
But there must be a cheap solution to this too... right?
Old Gopros! 
Old gopros are a proven low budget tool for high definition camera systems. They are able to handle all of the video compression by themselves and then transmit it either through WiFi or USB cable. Of course, for our underwater applications WiFi will not work, so cable it is.
<img width="1683" height="1086" alt="Screenshot 2026-08-31 at 11 19 13 AM" src="https://github.com/user-attachments/assets/9225e361-963f-4f62-a7d0-23ebcd41b40a" />
Next up was the propulsion system!
For this i designed a custom thruster case to fit my 980kv sunnysky BLDC motors. I wanted to be able to just copy and paste the thrusters so that I could easily model the whole thing around the same repeating geometry. For this reason I decided to make it a the shape of a barrel that can easily be replaced if anything corrodes or breaks.

My test of the thruster at low speed in my bathroom sink:

https://github.com/user-attachments/assets/cb4b14ec-2ffa-4109-a6d4-e576eac1fb48


I want this drone to be as immersive as possible, it should feel like you are a fish!
This is why I decided to go with a vectored 6 degrees of freedom configuration. I tried to replicate the configuration from the FiFish v6, a $1700 ROV that manages to achieve 6 independant degrees of movement with only 6 motors!
Here is my attempt at replicating the configuration: 
<img width="1728" height="1117" alt="Screenshot 2026-09-13 at 12 23 29 AM" src="https://github.com/user-attachments/assets/c6ad09c7-e0fa-4276-95b5-1aec722eeb0a" />
Next up was the electronics!

<img width="1728" height="1117" alt="Screenshot 2026-09-13 at 10 51 15 AM" src="https://github.com/user-attachments/assets/2cb76b6b-68b1-4fe8-8050-8f0c5e8bf7c1" />


This was the part I was dreading most and thankfully, I was able to find a good electronics schematic for a similiar project to what I was trying to do and I modified it to fit my design.
For the battery, I decided to go with a 3s3p custom pack using 9 lithium 18650 cells. Connected to the battery is a ____ A fuse and a pixhawk power sense module for extra safety.
For the Control system I went with the proven Pixhawk flight controller which allows me to control the complicated thruster configuration with ease through a program handled by the pixhawk. The pixhawk also reads the I2C protocol coming from a Depth sensor module which will come in very handy. Also, it acts as a safety mechanism allowing me to see the battery voltage, current draw, and it has a built in failsafe if the battery current goes too high.

<img width="1728" height="1117" alt="Screenshot 2026-09-13 at 10 56 53 AM" src="https://github.com/user-attachments/assets/db7d1b1d-cb41-4b6b-b616-d09b793f4222" />

The Rasberry pi is used as the companion computer to the pixhawk flight controller, it communicates through an ethernet cable to the surface computer giving the Camera feeds, depth information, power sensor information, IMU information, and temperature. 
To power the motors I use a 4 in 1 HackRC drone ESC and 2 single Littlebee ESCs, each channel is rated for 25A.
I also decided to mount a small 3d printer fan because these ESC's will get HOT!
Finally I wanted to include 4 LED's so I also mounted the drivers into the bottom of the configuration. 
The wires are then routed out of the 3d printed endcap, soldered together and then the solder joint is potted in epoxy for maximum pressure rating, then the ethernet cable goes into a WEIPU female connector to attach to the ethernet cable tether going up to the surface!
Thats about it for the electronics

All of the electronics fit inside of a 80ID x 90OD acrylic pipe that is 320 mm long
The endcaps are 3d printed and the cables are passed through with solder joints to stop capilary action up the cable insulation. Then the whole endcap, cable joints included, is potted in epoxy 

<img                                                                                      width="1728" height="1117" alt="Screenshot 2026-09-13 at 11 01 25 AM" src="https://github.com/user-attachments/assets/4ce61856-5adb-478c-aa15-e0ba51b20e5d" />



The part I was most looking forward to as an aspiring designer was the shell:
<img width="1728" height="1117" alt="Screenshot 2026-09-12 at 2 51 10 PM" src="https://github.com/user-attachments/assets/c846911d-11f5-4b87-aeff-00c2a211e770" />
This took me A LOT of time, about two weekends worth of not touching grass but I think it was worth it because the result is a hydrodynamic, easy to assemble (hopefully) very solid design that will print in a standard 256^3 mm 3d printer bed! 
The hardware needed for as
embly is minimal, about 50 m3 bolts and heat set m3 brass inserts 
As for the assembly, I designed it to be as easy as possible. All of the thrusters connect to the shell in 4 places so start by inserting heat set inserts into your thrusters, then screw
How the horizontal thrusters will screw into the shell:

https://github.com/user-attachments/assets/931fc479-a999-401c-849b-3841b58536d0

I also decided to go with a vectored LED lighting fixture for 4 5W LEDs that should give a wide floodlight when descending past the daylight or diving at night. These LEDs will not just be on or off, but they can be controlled by a PWM signal provided by the Pixhawk

<img width="1728" height="1117" alt="Screenshot 2026-09-13 at 10 39 18 AM" src="https://github.com/user-attachments/assets/c6408321-787f-47be-95d5-01ea40d12be8" />

The tether connects to the shell by a rear mounted WEIPU connector: 
<img width="1728" height="1117" alt="Screenshot 2026-09-13 at 10 47 37 AM" src="https://github.com/user-attachments/assets/f32b380e-94fe-4953-ab3c-e6119982cb38" />


Because the shell was too big to print in one piece, it divides nicely into a rear, and two halves of the front. Everything is secured with M3 screws that will make for a very sturdy connection between the different pieces: 

https://github.com/user-attachments/assets/647f90c3-3dfa-40e7-80a8-27e3c8544850

Thats it for the shell! 
For the software, I will just be using the standard Ardusub firmware downloaded onto the pixhawk flight controller, for the surface computer I will use QGround control to be able to control the whole thing with my PS4 controller and view the camera feeds in my oculus quest headset!



