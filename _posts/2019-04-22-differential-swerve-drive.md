---
categories: blog
layout: post
published: false
title: Differential Swerve Drive
---
Differential Swerve Drive is a project I started over a year ago. In FRC, Swerve Drive is a high risk high reward drivetrain type that combines the omnidirectional capabilitys of mechanum drive with the stealler traction of normal tank drive. The down side is the mechanical and programming complexity that is required to pull it off. For most teams it is simply not effort effective to use, but in recent years it has been becoming more popular. For example teams like Stryke Force, Jack in the Bot, and MadTown have all brought swerve to einstine finals.

Yes swerve drive is very cool, but I am not a fan of the bulky, heavy, and complicated modules. I would normally have never touched swerve drive but a [post on Chief Delphi](https://www.chiefdelphi.com/t/pic-differential-swerve-module-971/160525) caught my eye about a year and a half ago.
![]({{site.baseurl}}/images/87184d96156d92dc88a3e1ce8f5b0717c6e520d9_2_1035x750.jpeg)

At the time and to this day I am stunned with how clean and elegant this 971 module is. I was inspired to ~~copy~~ create my own version of the design and use it in MiniFRC 5. A friend and I worked on it a lot during our winter break in late 2017, even to the point where we got [a module working](https://youtu.be/14knHvExIa4) (Sorry for the poor video quality).
![]({{site.baseurl}}/images/DiffPic2.png)
We didnt end up using it in MiniFRC 5 because the modules are quite large, it would have been too much to try to fit even 3 modules within the frame limit, let alone other robot mechanisms. I plan to one day build a 3 module drivetrain. But until then I will go ahead and post the CAD here.

https://drive.google.com/open?id=1odAfKXtke28jzhcQ9p3HLBChvFibkNH_

Its mostly 3d printed, you may have to adjust the horizontal expansion setting on your printer as the tolerances are very tight. The only metal parts are 1/4in ball bearings, 5/8in OD bearings, and (most annoyingly) a 3/16 hex rod for the main axle. If I were to bring this project back I would honestly use plastic lego axles instead. The modules are built to run off of these [TT motors](https://www.aliexpress.com/item/TT-Motor-Smart-Car-Robot-Gear-Motor-for-Arduino-Free-Shipping-Wholesale/32642267017.html?spm=2114.search0604.3.3.762d2c77fhf1WS&s=p&ws_ab_test=searchweb0_0,searchweb201602_7_10065_10130_10068_10890_10547_319_10546_317_10548_10545_10696_453_10084_454_10083_10618_10307_537_536_10059_10884_10887_321_322_10103,searchweb201603_35,ppcSwitch_0&algo_expid=60a2a1c4-a1a0-4011-8f93-847c8594bbe1-0&algo_pvid=60a2a1c4-a1a0-4011-8f93-847c8594bbe1) but you could modify the small spur gears for any shaft. Whatever you use just make sure they have encoders or you will have a bad time. I cut a corner when designing the big ring gears. they are actually two gears (a beval gear and a spur gear) that need to be combinded before they are exported as an stl for printing.
![]({{site.baseurl}}/images/DiffPic1.png)
