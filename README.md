# Ek1254 -IR Infrared Sensor
# Purpose
- The purpose of this project is to reduce parking problems using Ek1254 sensor. Ek1245 infrared sensor will detect if there is any car parked in the parking spot.

<img src="https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/caseImage1.jpg" width="500" height="500">

## Table of Contents
1. [Introduction](#introduction)
2. [System Diagram](#system-Diagram)
3. [Materials](#materials)
4. [Budget](#budget)
5. [Time Commitment](#time-Commitment)
6. [Setting up Raspberry Pi](#setting-Up-Raspberry-Pi)
7. [Hardware Testing](#hardware-Testing)
8. [Mechanical Assembly](#mechanical-Assembly)
9. [PCB Soldering](#pcb-Soldering)
10. [Power Up](#power-up)
11. [Unit Testing](#unit-Testing)
12. [Production Testing](#production-Testing)
13. [Conclusion](#conclusion)


## Introduction
- IR Infrared Sensor can be widely used in obstacle avoidance car, line count, and black and white line tracking and so on.
- The module detects the distance 2 ~ 30cm, detection angle 35 °, the distance can detect potential is adjusted.
- The output port OUT sensor module can be directly connected to the microcontroller IO port, you can directly drive a 5V relay.
- It has a pair of infrared transmitting and receiving tube, tube infrared emit a certain frequency, when detecting direction meet with obstacles (reflecting surface), reflected infrared receiving tube, after the comparator circuit processing, green indicator will light up, at the same time signal output interface to output digital signal (a low level signal).
- Can be used for 3-5V DC power supply modules. It has red power indicator.



## System Diagram 

![systemdiagram](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/systemDiagram.PNG)

## Materials
- [Raspberry Pi](https://www.amazon.ca/CanaKit-Raspberry-Starter-Premium-Black/dp/B07BD56DW5/ref=sr_1_4?crid=1KYA5VN1D2732&keywords=raspberry+pi+3+starter+kit&qid=1576001973&s=electronics&sprefix=raspberry+pi+3+st%2Celectronics%2C150&sr=1-4) 
- [Ek1245](https://www.amazon.ca/gp/product/B07FFM7DYQ/ref=ppx_yo_dt_b_asin_title_o06_s00?ie=UTF8&psc=1) -IR Infrared Sensor
- Breadboard and [jumper wires](https://www.amazon.ca/dp/B01M1IEUAF/ref=dp_cerb_1) for initial testing
- [Socket Header](https://www.amazon.ca/gp/product/B07CWSXY7P/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1) to attach sensor and pi together on [PCB](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/pcb_frontSide.jpg).For production export it to the gerber files. 
- Case to hold ciruit together and prevent it from damage.Here is design of my [case](https://github.com/HarleenSaini19/parkingEaze/blob/master/mechanical/HKSPi3Case%20New.cdr).You can also check acrylic cases [here](https://www.thingiverse.com/search?q=raspberry+pi+3+laser&dwh=445defe2659844c).

## Budget
![capture](https://github.com/HarleenSaini19/parkingEaze/blob/master/images/Bugdet_Capture.PNG)

## Time Commitment
This project can be done in a week if one gives 2-3 hours a day. It will take about 2 to 4 days to recieve the parts. If you want to skip breadboarding then you can get started with the soldering which would take about 10 minutes but testing can take about 3-4 hours. After soldering is tested, it should take about 1-2 hours to power up the PCB and run the python script and get the readings.

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

## Power Up
After all the components are connected, your PCB should look like this.
![PCB_PowerUP](https://raw.githubusercontent.com/HarleenSaini19/parkingEaze/master/images/PCB_PowerUP.jpg) 

## Unit Testing

### Python Script
You can use the code underneath to get the readings from your sensor:
```
import RPi.GPIO as GPIO
from time import sleep

GPIO.setmode(GPIO.BCM)
GPIO.setup(4,GPIO.IN)


while True:
    sensor = GPIO.input(4)
    if sensor ==1:
        print("Parking Slot Available")
        sleep(1)

    elif sensor ==0:
        print("Parking Slot filled")
		sleep(1)
```


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
For mass production of this sensor, there are very rare chances of any drawbacks.The PCBs will be mass soldered and will be tested for connectivity at the end of the production line using a simple resistance test.For mass production testing it can be easily tested as when you will connect your sensor to raspberry pi without running the code you can see if there is any object which is in the range of the sensor the led of the sensor will glow this will tells you that you have done your soldering accurately.

## Conclusion
The project is easily reproducible by following the instructions. The project can be done using an Arduino, which costs less than the Raspberry Pi, however the steps that will be taken to create this project will be way different than the instructions explained above.


