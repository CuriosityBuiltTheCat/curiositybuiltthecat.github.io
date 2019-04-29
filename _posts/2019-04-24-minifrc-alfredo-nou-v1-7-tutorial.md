---
categories: blog
layout: post
published: false
title: MiniFRC Alfredo NoU V1.7 Tutorial
---
## ESP32s
We realized at kickoff that half of the ESP32s we bought were unusable due to them having the wrong pinouts, so we couldn't give them to teams. If you weren't able to get an ESP32, [you can buy ones with the right pinout here](https://www.amazon.com/gp/product/B071XP56LM/ref=ppx_yo_dt_b_asin_image_o00_s00?ie=UTF8&psc=1).

## Important safety information
1) The most important thing to do when getting started with your NoU is to plug the ESP32 in correctly. If you install the ESP32 incorrectly and power up the board you will likely fry your ESP32.

![]({{site.baseurl}}/images/plug%20it%20in%20right.png)

2) There are two kinds of 5V regulators on NoUs, DPARK and TO-220. The board was designed for TO-220 but our bulk order didn't arrive in time so most boards use a less powerful regulator, the DPARK. On DPARK NoU's motors should function no different than boards with the TO-220 but we recommend using no more than a single 9g servo. Under the right conditions you could use more but you do so at your own risk. We will receive our shipment of 220-regulators this week, once we do we will do two things to fix DPARK boards:
-we can swap the regulator on you board out for a TO-220
-you can trade in your whole DPARK board for a TO-220 board

![]({{site.baseurl}}/images/5v regs.png)

3)On NoUs, some areas of the board will get warm or hot depending on load. Be careful about touching these areas. If you put your finger on an area of the board and cant hold it there for more than 3 seconds **remove power from your board immediately and contact us**. Here are areas of the board to watch out for:

![]({{site.baseurl}}/images/image0.jpg)

## Getting started with the NoU
When uploading code to an ESP32 most of the steps are the same as an arduino. Installing the boards files (only do this once)

In the arduino IDE naviate to File > Prefrences and paste this link into the Additional Boards Manager URLs section:

https://dl.espressif.com/dl/package_esp32_index.json

it should look like this:

then naviage to Tools > Board > Boards Manager... and search for "esp32". install the board files by espressiff systems

it should look like this:

2) whenever you uploading code

you 








