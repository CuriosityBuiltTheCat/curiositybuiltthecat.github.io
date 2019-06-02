---
categories: blog
layout: post
published: false
title: MiniFRC Alfredo NoU V1.7 Tutorial
---
## ESP32s
We realized at kickoff that half of the ESP32s we bought were unusable due to them having the wrong pinouts, so we couldn't give them to teams. If you weren't able to get an ESP32, [you can buy one with the correct pinout here](https://www.amazon.com/gp/product/B071XP56LM/ref=ppx_yo_dt_b_asin_image_o00_s00?ie=UTF8&psc=1). (If you find a different listing be sure the pinout is correct).

## Important safety information
**The most important thing to do when getting started with your NoU is to plug the ESP32 in correctly. If you install the ESP32 incorrectly and power up the board you will likely fry your ESP32.**

![]({{site.baseurl}}/images/plug%20it%20in%20right.png)

On NoUs, some areas of the board will get warm or hot depending on load. Be careful about touching these areas. If you put your finger on an area of the board and can't hold it there for more than 3 seconds **remove power from your board immediately and contact us**. Here are areas of the board to watch out for:

![]({{site.baseurl}}/images/image0.jpg)

## 5V regulators
Every NoU has one of two diffrent packages of 5V regulator, DPAK and TO-220. The board was designed for TO-220 but our bulk order didn't arrive in time so most boards use a less powerful regulator, the DPAK. On DPAK NoU's motors should function no different than boards with the TO-220, but **we recommend using no more than a single 9g servo**. Under the right conditions you could use more but you do so at your own risk. Our shipment of 220-regulators should arrive later this week, once they do we will do three things to fix DPAK boards:
 - we can swap the regulator on you board out for a TO-220
 - you can trade in your whole DPAK board for a TO-220 board
 - we can give you a TO-220 regulator and you can swap the regulators yourself

![]({{site.baseurl}}/images/5v regs.png)
(image should say DPAK, not DPARK)

## Getting started with the NoU
You can use the Arduino IDE to upload code to the ESP32 by following these instructions. First you have to install the board files. In the arduino IDE navigate to File > Preferences and paste this link into the Additional Boards Manager URLs section:

https://dl.espressif.com/dl/package_esp32_index.json

It should look like this:

![json link.png]({{site.baseurl}}/images/json link.png)

Then navigate to Tools > Board > Boards Manager... and search for "esp32". install the board files by Espressif Systems.

It should look like this:

![boards manager esp32.png]({{site.baseurl}}/images/boards manager esp32.png)

Finally, watch the console when you go to upload code. After a couple of seconds "Connecting" along with dots and dashes will appear. When this happens press the "boot" button on the ESP32 and your code will be uploaded.

## Library and Default code

At [this](https://github.com/Dinokaiz2/Alfredo-NoU) link you can find our library and default code to help you get started with your NoU. It is currently under heavy development so expect updates in the coming days and weeks.

## Board CAD, dimensions, and schematic

[Alfredo NoU v1.7 SLDPRT](https://drive.google.com/open?id=1-XDGzYLNQDt2PNEBpxmt4ZZ6uxIaosUd)

[Alfredo NoU v1.7 STEP](https://drive.google.com/open?id=16myjRSVEqPulHQl5nlFSAyRZgfUEy22l)

![]({{site.baseurl}}/images/NoU 1.7 dims.png)

![]({{site.baseurl}}/images/unknown-1.png)
