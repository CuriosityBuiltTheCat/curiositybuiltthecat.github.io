---
categories: blog
layout: post
published: false
title: PyroBot at the Trinity College International Fire Fighting Robot Contest
---
## The Goal
the _Trinity College International Fire Fighting Robot Contest_ is A yearly event at which robots are tasked with navigating a simple maze and extingishing a candle somewhere within as quickly as possible. on April 12th I flew up to Hartford Conneticuit to Compete with my robot: Pyrobot. ![pyrobot final.PNG]({{site.baseurl}}/images/pyrobot final.PNG)
The pyrobot in this picture is very diffrent from the one I flew out with. I had high hopes for PyroBot but as usual, everything is twice as hard as you think it will be. Despite the setbacks I am happy with the project as I was able to pull off a small victory in the end.

### The Rules
I won't go into too much detail but the gist is, you are allowed to do five total runs and there are three levels. You may only attempt a harder level once you have completed the one before it. You get 600 points for each level you dont complete (lower scores are better). Your total final score is the sum of your best scores on each level. Level 1 is the most simple. You know where all the walls will be and the only obstical is a stuffed animal randomly placed at one of 3 locations. Level 2 adds carpets, multiple wall conifgurations, and "decorations" on some of the walls (ie. Mirrors and fabric). In level 3 they combine two mazes and start you randomly in the first. The goal is two blow out three candles in the second maze as well "rescue a baby" (move a doll from the second maze to the first).

### The Plan
A friend and I began work on our stratagy over 2 months ago. At first the plan was to do almost everything and do it in the style of a micromouse robot. We noticed that most of the robots at past competitions were relativle slow (except for this bot from china, by far) but even the Chinese robot doesnt compare to the speed of a micromouse. I splurged on some of the expensive IR LEDs ([sfh4545](https://www.digikey.com/product-detail/en/osram-opto-semiconductors-inc/SFH-4545/475-2919-ND/2205955?utm_adgroup=Optoelectronics&slid=&gclid=CjwKCAjwzPXlBRAjEiwAj_XTEY_Bn_ii0FJhxkulefOmwNh326yjtMyb8GEm5WsBmxhUt5ty_riYpBoCXm8QAvD_BwE)) and phototransistors ([teft4300](https://www.mouser.com/datasheet/2/427/teft4300-84750.pdf)) used by many micromice for distance sensing. The "go to" motors for micromice were a bit out of my price budget so I went with some agreesivly geared N20 motors that had intagrated encoders. The Motors were driven by a chip I am very familar with, an L293D Dual H-Bridge. There is really no limit on what fan you are allowed to use to blow out the candle so I chose to use the BLDC motor off of a RC plane I once built. Next I chose the battery. After some testing with a 7.4V (2 cell) battery I wasent happy with the speed of the robot so I decided to use a 11.1V (3 cell) battery instead, which also improved our fan preformance. To control the robot I considered useing an esp32, but ultimatly went with an arduino nano because if its size and I was familar with it. Again inspired by MicroMice, I chose to make the chassis of the robot a custom circuit Board, Fabricated on an OtherMill at my universitys maker space. Finally we figured finding the candle was a great vision processing task and planned to use my friends Jvois Vision processing camera with an IR pass filter. After carefully designing the 3dprinted parts, a circuit board and soldering some tedious wires, we thought we had the hardest problems solved.

## The Problems
### The nanos
I figured from the start it would take two iterations to design the circuit board: an initial prototype and a final with all the kinks worked out. However when I was designing the robot I made a fatal error. In order to save space I hung the nano underneath the robot where there was not enough vertical space for female headers, meaning that I soldered the nano directly to the circuit board. This had the awful side effect that if we ever fried a nano, we had to replace the entire chassis. You may think Im stupid for even attemping a stratagy like that, but to be fair it has worked great for me before on one of my combat robots. The diffrence between that project and this one is the combat robot was less complex and ran on much less than 12v. After 3 bricked chassis I gave up on the hanging method and moved the nano to the top of the board with female headers. this ended up being the right choice by far as I fried 2 more nanos during developement that I was able to "hot swap" out. Unfourtunatly by the time I made this switch we had lost 5 days (its hard to mill these boards) and I only had time to make a use the first itteration of the "hotswap" design. 

### Voltage regulation
the third nano I fried by supplying 12V to vin. The documentation says that nanos can run off of 12V but I looked into it and it seems that the 5V linear voltage regulators on chinese clones can handle only around 7V to 10V. It was at this point I said "screw it" and added not one but three switch mode regulators to the robot: a 7.5V reg to keep the nano happy, a 5V reg for the Jevois as it could draw up to an Amp, and a 3V reg for the IR LEDs. I was going to power the LEDs off the the arduinos 3.3V line but they too draw a decent amount of current and I wanted to reduce the strain on the nano as much as possible.

### The Boards
On top of the strategic errors surrounding the custom boards, the boards themselves were of poor quality and cause many issues. It was a pain to design them because any jump from one side of the board to the other has to be done with vias, for example all of the arduino headers could only be soldered/accessed on the bottom of the board. The most common physical issue is a trace would break (or in some cases fry) and I would have to run a wire to jump the connection. The worst issue was at one point I ripped about 6 pads off of one section of the board and had to do some very janky wiring to fix it.

### The Jevois
If the other issues were thumb tacks, this issue felt like a train spike in the coffin. We only got the robot fully together a couple of days before the competition. At this point we knew we couldnt "do everything", but we at least felt like we could still be competitive.![pyrobyte_all_together.jpg]({{site.baseurl}}/images/pyrobyte_all_together.jpg)
It was then that had had to drop the Jevios. While my friend could get it to find the candle excelently when plugged into the robot, we could not for the life of us get it to spit any of its data out over serial. We worked on this issue till 4:00AM the night before my flight and to this day we dont know what the problem was. I flew into Hartford with a robot that could barely naviage a maze and not only had never seen a candle before but at that point was totally blind.

## The Bodge
### Hardware
When I started this project I pictured rolling up to Hartford with a beatiful well crafted robot that was basically a Micromouse with a fan on it. I'm very much a prefectionist; the robot would be a clean, meticulously designed, and well crafted machine. On Friday night a switch flipped in my head and my mentality changed. I couldnt let perfect be the enemy of good and I just wanted to have the robot work at all. There were minor electrical issues to fix but the main issue was finding and pointing twords the candle. _At the hotel_ I canbalized some of the ir distance sensors off of the frount of the robot and repurposed their photo transistors to instead look for the candle. I arrived at the competition site at 7:15 and was the first person inside the venue. After I set up my pit I spent the next 4 hours fixing minor electrical issues and preparing my robot to be inspected before noon. I knew the bot I had built was small, but at the inspection table I was told my bot was one of the smallest the inspectors had ever seen. I realized that if I could just complete a single run, I would likely win the _tiny robot contest_, doing so became my primary and only goal. 

### Software
By 1:00pm I was feeling good about my progress. There after minor electrical issues perodically popped up, but I was able to turn most of my attention on software. I had to throw out a lot of the code I brought with me. We origially planned to move through the maze using a PID based planned path, but now that I didnt care about my score and time was a huge issue I changed my aproach to that of a blind search. My stratagy had 3 parts:

- A simple right wall following PID-loop using the robots front right distance sensor (this worked well because if the right wall ever "fell away" the robot would turn sharply right)
- The robot used its last remaming forward facing distance sensor to check if it was about to run into a wall. If a wall was detected it would back up, turn 90 degrees left, and continue to follow the wall.
- The robot would periodically turn off its IR LEDs and look for IR light. If it detected light above a threshold it knew the candle was nearby, at that point the main loop was done and the robot just had to blow out the candle.

The first Item on this list was the most difficult to implement. I spent a good amount of time trying to tune parts of my PID-loop: the terms, the max speed and the output limits. After awhile I got a legendary suggestion from one of the other compeditors, _rotate the sensor 45 degrees forward_. I rotated the sensor and increased my setpoint, it was like magic. It followed the wall and turned right when the right wall fell away on the first try. I still tuned the PID a bit more but for me it was a small victory after a long list of failures. After that the frount wall detection got working in no time, [here](https://youtu.be/k0aB9E2kX8I) is the robot with the two behaviors combined. 

The third part of my stratagy worked quickly as well. Using the three photo transistors the robot could reliably find and even point at the candle. The main issue was the robot had a hard time knowing how far away from the candle it was. I never came up with a cool solution to that problem, I just programed it to drive forward and backward till the candle was out.

### The last big hurdle
By 4:00 on saturday I was feeling good but still nervous as if I didnt attempt my first two runs by 5:15 they went down as DNFs. I was all set to do a couple more practice runs and then head to the competition fileds when I got hit with a final terrible problem, my BLDC motor wouldnt spin! I spent the next hour and 15 minutes trying diffrent PWM signals, eliminating any potential mechanical issues and I even swaped out the ESC but it never got up to speed. I lost the chance to attempt 2 of my 5 runs and left the event for the day.

### Sunday
Sunday was crunch time. I gave up on the BLDC motor and resolved to use a diffrent motor I brought, an impellar fan. I canbalized a spare L293D into basically a mosfet and tacked on the fan with hot glue. I had more sucess than with the BLDC motor (including my first sucsessful unassitsed practice run) but it was not very powerful and not reliable at all. I ended up borrowing a motor and broken fan from another team. I added a "counterweight" to fix the broken fan and that was the last big problem solved. From then on I was just testing and tuning. For me that was the most fun I had; tweaking IR threshholds, time delays, and PID values untill I was satisfied with my robots consitancey. By 1:00pm I was ready for my first run

### Attempt 1
I'll cut to the chase, It Worked! Lucky for me the candle was in the first room my bot looked inside (although at that point PyroBot could search almost the entire maze). I was stoaked both because it was incredible how much work it took to just get to that point, and also it ment that I basically had the tiny robot contest in the bag. I foolishly forget to record the run, but afterwards I recorded a [recreation with the same starting conditions](https://youtu.be/EnO5fbiQ0Gs).

### Attepts 2 and 3
I didnt make any changes for my second run, now in level 2. The run failed because the robot got stuck on the carpets. The drivetrain was already geared to be high speed and low torque, but on top of that I was running the drivtrain at no more than 40% of its max speed. I bumped the drivetrain up to 60% power, but this messed up my PID and turn left function. I re-tuned both parts of the control logic but didnt have the time to thourghly test it. In my third and final attempt PyroBot had no problems with  the carpets, but it ended up getting stuck in one of the rooms and failing the attempt.

### Closing ceremonies


## 










