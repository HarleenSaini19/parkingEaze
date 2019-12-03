# Ek1245 -IR Infrared Sensor
 
<img src="https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/caseImage1.jpg" width="500" height="500">

## Table of Contents
1. [Introduction](#introduction)
2. [Purpose](#purpose)
3. [System Diagram](#system-Diagram)
4. [Materials](#materials)
5. [Budget](#budget)
6. [Time Commitment](#time-Commitment)
7. [Setting up Raspberry Pi](#setting-Up-Raspberry-Pi)
8. [Hardware Testing](#hardware-Testing)
9. [Mechanical Assembly](#mechanical-Assembly)
10. [PCB Soldering](#pcb-Soldering)
11. [Unit Testing](#unit-Testing)
12. [Production Testing](#production-Testing)


## Introduction
- IR Infrared Sensor can be widely used in obstacle avoidance car, line count, and black and white line tracking and so on.
- The module detects the distance 2 ~ 30cm, detection angle 35 °, the distance can detect potential is adjusted.
- The output port OUT sensor module can be directly connected to the microcontroller IO port, you can directly drive a 5V relay.
- It has a pair of infrared transmitting and receiving tube, tube infrared emit a certain frequency, when detecting direction meet with obstacles (reflecting surface), reflected infrared receiving tube, after the comparator circuit processing, green indicator will light up, at the same time signal output interface to output digital signal (a low level signal).
- Can be used for 3-5V DC power supply modules. It has red power indicator.

## Purpose
- The purpose of this project is to reduce parking problems using Ek1254 sensor. Ek1245 infrared sensor will detect if there is any car parked in the parking spot.


## System Diagram 

![systemdiagram](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/systemDiagram.PNG)

## Materials
- Raspberry Pi
- Ek1245 -IR Infrared Sensor
- Breadboard and jumper wires for initial testing
- Socket Header to attach sensor and pi together on PCB
- Case to hold ciruit together and prevent it from damage

## Budget
![capture](https://github.com/HarleenSaini19/parkingEaze/blob/master/images/Bugdet_Capture.PNG)

## Time Commitment
This project can be done in a week if one gives 2-3 hours a day. It will take about 2 to 4 days to recieve the parts. If you want to skip breadboarding then you can get started with the soldering which would take about 10 minutes but testing can take about 3-4 hours. After soldering is tested, it should take one more 1-2 hours to power up the PCB and run the python script and get the readings.

## Setting up Raspberry Pi
First step after getting your raspberry pi is to set it up. Follow the steps below:
1. Download [Raspbian](https://www.raspberrypi.org/downloads/) to be installed on your raspberry pi.
2. Use [SDCardFormatter](https://www.sdcard.org/downloads/formatter_4/) to format your SD card and flash downloaded OS on your SD card.
3. Insert SD card in raspberry pi and connect the side devices like keyboard and mouse.
4. Switch on the power and finish the further setup.

## Hardware Testing

After software installation, i made the connections using jumper wires from sensor to breadboard and breadboard to raspberry pi.

Wiring:
---
- Raspberry Pi 3V  to sensor VCC
- Raspberry Pi GND to sensor GND
- Raspberry Pi GPIO4 to sensor OUT

Since there is no SCL and SDA pin.Therefore, there will be no i2c bus address


### Raspberry Pins
This wiring diagram could be helpful to make the connections on breadboard
![fritz_bb](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/HarleenSaini_parkingEazeV1_bb.png)


## Mechanical Assembly
Either you can connect you pi to your sensor using breadboard connections or you can solder your sensor.
Breadboarding is just to check if sensor works as expected or their is a need to change some connections or if there is a damaged component.

| EK1254| Raspberry Pi |
| ----- | ----- |
|  VIN  |  3V   |
|  GND  |  GND 	|
|  OUT 	|  GPIO4|




## PCB
Here is my PCB Design:
![fritz_pcb](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/HarleenSaini_parkingEazeV1_pcb.png)

After soldering my pcb, it looks like this:
![pcb](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/pcb_frontSide.jpg)
there are socket headers to connect raspberry pi and sensor to the pcb.

### Power Up
After all the components are connected, your PCB should look like this.
![PCB_PowerUP](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/PCB_PowerUP.jpg) 

## Unit Testing

### Python Script
You can use the code underneath to get the readings from your sensor:
![python_script](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/python_script_capture.PNG)

### Final Testing
Running python script will get you the readings
![reading](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/Code_output.png)

### Enclosure
If your raspberry pi is working with the sensor and you are getting  readings then you can go further and make your acrylic case to prevent your raspberry pi and sensor from getting damaged.


If you are successful in making your case, it should look like this.
![design1](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/caseImage1.jpg)
![design2](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/caseImage2.jpg)
![design3](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/caseImage3.jpg)
![design4](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/caseImage4.jpg)



## Production Testing
For mass production of this sensor, there are very rare chances of any drawbacks. There could be a problem while buying sensor as it could be sold out. Raspberry pi and all the other objects used in this project are easily available.


