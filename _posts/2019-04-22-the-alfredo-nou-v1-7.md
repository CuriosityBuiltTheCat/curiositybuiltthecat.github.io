---
categories: blog
layout: post
published: true
title: The Alfredo NoU V1.7
---
Classically, MiniFRC Robots have been run using the combination of an Arduino Uno, An Adafruit Motor Shield v1, and an HC-06 Bluetooth chip. While this system has worked well for many robots over the last two years, it has a couple key issues that are not ideal.

### 1) Wires for the HC-06 chips have to be soldered to the motor shield
Not a big issue but this process can be a roadblock for new teams looking to jump right into robot building. On top of that, weak Dupont headers can cause disconnects during matches.

### 2) SoftwareSerial and servos
In order to talk to the HC-06 chips, the built it library SoftwareSerial is used. SoftwareSerial interferes with the default Servo library, making servos unusable. One workaround for this is to use the SimpleSofwareServo library, but even then servos can be jittery.

### 3) The Adafruit motor shield only supports two servos
If anyone wants to use 3 or 4 servos you have to breakout PWM pins, 5V, and GND yourself, yuck!

## the solution: Introducing the Alfredo NoU!

![]({{site.baseurl}}/images/IMG_20190415_203423.jpg)

This alternative controls system consists of two boards: an ESP32 Devkit board, and The Alfredo NoU V1.7. This system has some significant improvements over the Arduino based system:

- The ESP32 had bluetooth built-in, meaning there is no need for HC-06 chips or SoftwareSerial.
- the board supports **4 servos**, twice as many as the Adafruit motor shield.
- The lack of SoftwareSerial combined with beefy 5V regulators specifically for servos means that servos are more powerful and less jittery than ever.
- We will have a custom library available so that using the NoU will be even easier than Arduino and will have more features.
- The ESP32 is just as easy to program as an Arduino and can be programmed through the Arduino IDE.
- The NoU can drive four DC motors, just like the Adafruit Motor shield

At kickoff, you will have the option to receive an ESP32 and NoU V1.7 instead of the classic Arduino system in your KOP. If you have any questions about the board or the ESP32 feel free to email me at jrw4561@gmail.com or ping me on discord @Jacob#4883 ('@Jacob | FAST' on the MiniFRC Discord).
