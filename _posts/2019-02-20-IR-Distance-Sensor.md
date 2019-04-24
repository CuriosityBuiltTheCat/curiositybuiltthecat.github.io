---
categories: blog
layout: post
published: true
title: IR Distance Sensors
---
One of the most important things an autonomous robot must be able to do is see and understand its surroundings. There are many ways to accomplish this. If you have a lot of time or money to blow, you could use LIDAR or vision processing but these systems are often unnecessary.

![]({{site.baseurl}}/images/HC-SR04.jpg){:height="120px" width="120px"}

In the past, I have used the ever-popular HC-SR04 ultrasonic distance sensor modules, however for an upcoming project I need something less bulky and more precise. I want to use IR distance sensors. IR distance sensors have two main components, an IR LED and an IR phototransistor. The LED shines on a nearby surface while the phototransistor measures how much of the IR light bounces back. A while back I bought some digital IR distance sensors off [amazon](https://www.amazon.com/OSOYOO-Infrared-Obstacle-Avoidance-Arduino/dp/B01I57HIJ0/ref=sr_1_4?ie=UTF8&qid=1550812474&sr=8-4&keywords=ir+distance+sensor) but I needed an analog sensor. I cannibalized an LED and phototransistor from one of the Amazon modules and built a prototype. Here is my schematic:

![IRsensorSchematic.png]({{site.baseurl}}/images/IRsensorSchematic.png)

I didn't have any 100-ohm resistors so I used two 200-ohm resistors in parallel. Here is the sensor:

![IMG_20190221_234129.jpg]({{site.baseurl}}/images/IMG_20190221_234129.jpg)

3.3V is blue, GND is green, and analog out is yellow. I know my colors are all wrong, but I was working with what I had.

The output from an IR distance sensor is not useful because the output is inversely proportional to the distance it measures. To get useful output data I roughly followed the steps on [this](https://home.roboticlab.eu/en/examples/sensor/ir_distance) webpage. Basically, you can convert the analog data into distance using this equation:

distance = (1 / (a * analogIn + b)) - k

I wasn't super concerned about precision in this proof of concept so to find a, b, and k, I measured some known distances and recorded the corresponding analog output:

| Analog value (0-1023) | Distance (mm) |
|-----|:--:|
| 971 | 20 |
| 810 | 25 |
| 440 | 60 |
| 270 | 120 |
| 210 | 240 |
| 192 | 300 |

I set up the data, variables, and distance function in a [desmos](https://www.desmos.com/calculator/15avgps3ai) plot and adjusted my a, b and k until the plot fit the points:

![analogIn vs distance.PNG]({{site.baseurl}}/images/analogIn vs distance.PNG)

I ended up with a = 0.000043, b = -0.005, and k = 15. In order to make the calculation a little easier on your microcontroller the roboticlab page recommened rearanging some of the terms:

| distance = (1 / (a * analogIn + b)) - k            |
| distance = (1 / a) / (analogIn + B / a) - k        |
| solving for 1/a and B/a, I got this final formula: |
| distance = (16667 / (analogIn - 133)) + 15         |

Now that I was reading distance (which was pretty cool by itself) I wanted to implement it on a robot. This chassis is from a previous project, a fairyweight combat robot with a custom controls system. I plan to one day document that project on this blog, but for now just know that it uses an Arduino Pro Mini as the "brain" and an L293D dual H-bridge for driving the motors (these components are underneath the robot).

![IMG_20190219_203939.jpg]({{site.baseurl}}/images/IMG_20190219_203939.jpg)

In the first test, I wanted to have the robot maintain a constant distance from whatever was in front of it. It drove forward until it was 20mm from a wall if it became closer than 20mm it would back up. This is called bang-bang control and it was essentially useless as the robot oscillated dramatically. To improve performance I switched it to a PD loop and added a rolling average for the analog inputs. This produced [much better results](https://youtu.be/YmUQSCi_pgA).

There is a lot that can be improved but for now, I am going to call this a success, in my next test I am going to rotate the sensor 90 degrees and see if I can get it to follow a wall while remaining a constant distance from it.

