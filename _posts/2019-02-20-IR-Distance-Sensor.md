---
categories: blog
layout: post
published: true
title: IR Distance Sensors
---
One of the most important things an autonamous robot must be able to do is see and understand its suroundings. There are may ways to acomplish this. If you have alot of time or money to blow you could use LIDAR or vision processing, but these systems are often unnessiscary.

![]({{site.baseurl}}/images/HC-SR04.jpg){:height="120px" width="120px"}

In the past I have used the ever popular HC-SR04 ultrasonic distance sensor modules, however for an upcoming project I need something less bulky and more precise. I want to use IR distance sensors. IR distance sensors have two main components, an IR LED and an IR phototransistor. The LED shines on a nearby surface while the phototransistor measures how much of the IR light bounces back. Awhile back I bought some digital IR distance senors off of [amazon](https://www.amazon.com/OSOYOO-Infrared-Obstacle-Avoidance-Arduino/dp/B01I57HIJ0/ref=sr_1_4?ie=UTF8&qid=1550812474&sr=8-4&keywords=ir+distance+sensor) but now I want an analog output. I canablized the LED and phototransistor and built a prototype based off of some recommended resistor values I found online. Here is my schematic.

![IRsensorSchematic.png]({{site.baseurl}}/images/IRsensorSchematic.png)

I didnt have any 100 ohm resistors so I used two 200 ohm resistors in parallel. Here is the sensor.

![IMG_20190221_234129.jpg]({{site.baseurl}}/images/IMG_20190221_234129.jpg)

3.3V is blue, ground is green, and analog out is yellow. I know my colors are all wrong :p I was working with what I had.

The analog output produced by any IR sensor is inversly proportional to the distance it measures which means that IR sensors are more acurate the smaller the distance and the data is not imediatly useful. To get useful output data I roughly followed the steps on [this](https://home.roboticlab.eu/en/examples/sensor/ir_distance) webpage. The gist of it is, you can convert the anlog input into distance using this equation:

distance = (1 / (a * analogIn + b)) - k

I wasent super concerned about precision in this proof of concept so to find a, b, and k I measured some known distances and recorded the corrisponding analog output.

| Analog value (0-1023) | Distance (mm) |
| ----------- | ----------- |
| 971 | 20 |
| 810 | 25 |
| 440 | 60 |
| 270 | 120 |
| 210 | 240 |
| 192 | 300 |

I set up the data, variables, and distance funtion in a desmos plot and adjusted my a, b and k until the plot fit the points.

![analogIn vs distance.PNG]({{site.baseurl}}/images/analogIn vs distance.PNG)








