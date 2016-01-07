---
layout: page
title: Bio-mimetic underwater robotics
---

***

##Challenges in bio-mimetic underwater robotics
Underwater robots are becoming increasingly important to naval and maritime science operations. Not only are larger, torpedo-sized robots important for things like mine-hunting, but smaller, fish-sized robots are important for fitting into tight spaces for inspections or to observe wild-life. Seaborne robots must be robust and durable to survive in the harsh ocean environment, and many applications for smaller robots also require agility and speed. An exciting way to achieve agility and speed is to create bio-mimetic robots, or robots that mimic the swimming mechanics of fish and other sea creatures (e.g. stingrays, squid). For example, MIT developed the RoboTuna in the 1990's to demonstrate the potential of fish-inspired underwater vehicles.

In the past, biomimetic underwater robots (e.g. robotic fish or stingrays) relied on segmented body designs, where each segment is individually actuated, to bestow agility and speed on their designs. For example, a fish tale would be made up of several segments, each of which would be controlled by a servo motor. Unfortunately, these segmented designs are not robust and suffer from high failure rates. Segment assemblies can fail, motors can burn out, or controllers and power sources can become overwhelmed.

##Under-actuated flexible bio-mimetic robots

At MIT, I was part of a team that designing a bio-mimetic underwater robots, including fish, stingrays, and salamanders. Our designs sought to solve the durability and failure issues of other bio-mimetic robots. They used one or two actuators, and relied on the mechanics of soft polymer bodies to create extra degrees of motion that resulted in underwater thrust.

Our [IEEE conference paper](https://dspace.mit.edu/handle/1721.1/79685) is available from DSpace@MIT, detailing our work on the bio-mimetic stingray.

###Developing a bio-mimetic stingray

The bulk of my work focused on building a small bio-mimetic stingray.

<p align="center">
<img src="/images/2016-01-05-stingray.png" alt="Bio-mimetic stingrays." width="400">
</p>

####Physical construction

Our stingray was constructed of a soft polymer body with only two actuators. We designed and 3D printed a lightweight skeleton that anchored the servo motors that provided thrust. The skeleton also provided the requisite rigidity as well as ballast control for the body of the stingray. To fabricate the stingray, we positioned the skeleton inside of a mold, and then cast the soft polymer body around it. Our prototypes were tethered by wires powering and controlling the servo actuators. We experimented with using different densities and flexibilities of polymer to control the waves created on the stingray wings.

####Software controller

I designed and demonstrated the control and actuation system to enable forward and backward motion and turning using only the two actuators. Attached to the servo motors that were anchored to the body were two levers that stretched into the wings of the stingray. By moving the levers up and down, the wings would flap, creating a wave that traveled along the stingray's wing, creating thrust that propelled the robot through the water. By varying the amplitude, frequency, and phase of the actuators in the two wings, I could control the forward, backward, and turning motions of the stingray in the water. I built the controller using Arduino, and designed a GUI interface for controlling the robot through a serial port in Processing and later in Python.

####Experiments and testing

We designed a video tracking system to measure the performance of the stingray prototypes. We used Matlab to quantify the movement of a series of points along the wing of the stingray, experimentally optimizing the necessary frequencies and amplitudes for the controller.

###A bio-mimetic salamander

I also built and tested a robotic salamander that could both swim and walk. Constructed of a soft polymer body and tail and rigid legs, it was also powered by two servo motors. One was used during swimming, and both were used to create a walking motion. We only conducted preliminary tests on a couple of salamander prototypes, and focused our efforts on the stingray.
