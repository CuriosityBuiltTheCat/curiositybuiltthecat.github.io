---
categories: blog
layout: post
published: true
title: IR Distance Sensors
---
One of the most important things an autonamous robot must be able to do is see and understand its suroundings. There are may ways to acomplish this. If you have alot of time or money to blow you could use LIDAR or vision processing, but these systems are often unnessiscary.

![]({{site.baseurl}}/images/HC-SR04.jpg){:height="120px" width="120px"}.

In the past I have used the ever popular HC-SR04 ultrasonic distance sensor modules, however for an upcoming project I need something less bulky and more precise. I want to use IR distance sensors. IR distance sensors have two main components, an IR LED and an IR phototransistor. The LED shines on a nearby surface while the phototransistor measures how much of the IR light bounces back. Awhile back I bought some digital IR distance senors off of amazon but I wanted an analog output. I canablized some of the components and built a prototype based off of some recommended resistor values I found online. Here is my schematic.

![IRsensorSchematic.png]({{site.baseurl}}/images/IRsensorSchematic.png)

I didnt have any 100 ohm resistors so I used two 200 ohm resistors in parallel. Here is the sensor.

![IMG_20190221_234129.jpg]({{site.baseurl}}/images/IMG_20190221_234129.jpg)

3.3V is blue, ground is green, and analog out is yellow. I know my colors are all wrong :p I was working with what I had.




