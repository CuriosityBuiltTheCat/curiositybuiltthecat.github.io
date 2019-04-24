---
categories: blog
layout: post
published: true
title: The Alfredo NoU V1.7
---
Classically, MiniFRC robots have been run using a combination of an Arduino Uno, an Adafruit Motor Shield v1, and an HC-06 Bluetooth chip. While this system has worked well for many robots over the last two years, it has a couple of key issues that are not ideal.

### 1) Wires for the HC-06 chips have to be soldered to the motor shield
This is not a big issue, but this process can be a roadblock for new teams looking to jump right into robot building. On top of that, weak Dupont headers can cause disconnects during matches.

### 2) SoftwareSerial and servos
The built it library SoftwareSerial is used to talk to the HC-06 chips. SoftwareSerial interferes with the default Servo library, making servos unusable. One workaround for this is to use the SimpleSofwareServo library, but even then servos can be jittery.

### 3) The Adafruit motor shield only supports two servos
If you want to use 3 or 4 servos, you have to breakout PWM pins, 5V, and GND yourself. Yuck!

## The Solution: Introducing the Alfredo NoU!

![]({{site.baseurl}}/images/IMG_20190415_203423.jpg)

The alternative control system consists of two boards: an ESP32 Devkit board, and the Alfredo NoU V1.7. This system has some significant improvements over the Arduino based system:

- The ESP32 has Bluetooth built-in, eliminating the need for HC-06 chips or SoftwareSerial.
- The board supports **4 servos**, twice as many as the Adafruit motor shield.
- The integrated Bluetooth combined with beefy 5V regulators designed for servos means that servos are more powerful than ever and have _zero_ jitter.
- The ESP32 is just as easy to program as an Arduino and can be programmed through the Arduino IDE.
- The Alfredo NoU can drive four DC motors, just like the Adafruit Motor Shield.
- COMING SOON: We will have a custom library available so that using the NoU will be even easier than Arduino and will have more features.

At the Spring 2019 MiniFRC kickoff, you will have the option to receive an ESP32 and NoU V1.7 instead of the classic Arduino system in your KOP. Up to 20 Alfredo NoU boards will be distributed at the event. If you have any questions about the board or the ESP32 feel free to email me at jrw4561@gmail.com or ping me on discord @Jacob#4883 ('@Jacob \| FAST' on the MiniFRC Discord).
