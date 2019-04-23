---
categories: blog
layout: post
published: false
title: The Alfredo NoU V1.7
---
Classically, MiniFRC Robots have been run using the combination of an Arduino Uno, An Adafruit Motor Shield v1, and an HC-06 Blutooth chip. While this system has worked well for many robots over the last two years, it has a couple key issues that are not ideal.

## Wires for the HC-06 chips have to be soldered to the motor shield
Not a big issue but this process can be a road block for new teams looking to jump right into robot building. On top of that, weak dupont headers can cause disconnects during matches.

## SoftwareSerial and servos
In order to talk to the HC-06 chips, the built it library SoftwareSerial is used. SoftwareSerial interfers with the default Servo library, makeing servos unusable. One work around for this is to use the SimpleSofwareServo library, but even then servos can be jittery.

## The Adafruit motor shield only supports two servos
If anyone wants to use 3 or 4 servos you have to breakout pwm pins, 5V, and GND yourself, yuck!

### the solution, introducing the Alfredo NoU V1.7!


