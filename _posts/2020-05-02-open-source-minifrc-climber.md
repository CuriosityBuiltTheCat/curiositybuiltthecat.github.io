---
categories: blog
layout: post
published: true
title: Open Source MiniFRC Climber
---
![IMG_20200502_131455.jpg]({{site.baseurl}}/images/IMG_20200502_131455.jpg)
    
MiniFRC has an interesting history of end-game tasks. The interest lies in the fact that in most games, no more than one or two robots ended up regularly completing them. Climbing the tower in the Stronghold game was never attempted. A handful of robots could climb in Power Up and Deep Space but not many. The one exception was the 2017 game, which used the Steamworks rope climbing endgame task. Nearly half of robots that year could climb, likely because building a winch with velcro is much easier than any of the mechanisms needed in other years.

My point is that end-game tasks in MiniFRC are hard, and MiniFRC: Infinite Recharge is no exception. I created and posted this design because I am hoping to see a lot of climbing robots this year. B) 

![Minifrc climber skdwrks.png]({{site.baseurl}}/images/Minifrc climber skdwrks.png)

[SLDPRT zip](https://drive.google.com/open?id=1ETVyFEv6Q3soigAOWNp2srHNfdwMz0kP)

[STEP Files](https://drive.google.com/open?id=10dSCo-1z4OkrMnQXhlyaSgPcRo47-Iiw)

[STL zip](https://drive.google.com/open?id=1UNVwLxh0FrK7LA274SeD1Ul8pp816zmP)

I want to make this design parametric and clean it up more, but I figured I should go ahead and make what I have public. The design consists of three main 3d printed parts: a mount, the rack, and a pinion. I intentionally left no bolt holes or anything on the mount, you can CAD on your own or just hot glue it to your chassis. The rack and the pinion require some decent tolerances, you may need to adjust your printers XY-compensation to have them print correctly. All parts should be printed without support material. Assembly is fairly straightforward, don't forget to add a couple zipties to keep the climber together.

As for the motor, I used a 290 RPM N20 motor for all of my testing. In theory you could use a 650 RPM motor if your robot is under ~1 kg but it’s probably not worth it. Even the 290 RPM motor lifts my 700g test chassis in about a second.

Motor          Torque            Torque/pitch radius = maximum force
290 RPM	       1.55 kg-cm        2.03 kg
650 RPM        0.75 kg-cm        0.98 kg
1350 RPM       0.25 kg-cm        0.32 kg
