---
layout: page
title: Mechanical engineering projects at MIT
---

I greatly enjoyed my experience as an undergrad and grad student at MIT. One of my favorite things about MIT is the opportunity to do a wide variety of projects and the resources to actually make them happen. These are some of my favorites.

+ [Long-term underwater power sources](#uuv-power): Designing and building UUV power sources at MIT for Lincoln Labs. Engineering and managerial roles
+ [Indoor robot positioning and navigation](#robo-nav): Creating a navigation system for a distributed network of sensor-carrying robots
+ [Yoyo manufacturing](#yo-yo): Designing and manufacturing 500 toy yoy-os that look like a mouse running in a hamster wheel
+ [Temperature profiles of found firearms](#gun-temps): Helping police to provide evidence of recent possession of firearms based on temperature

****

## <a id="meche"></a> Long-term underwater power sources

A critical barrier to wide-spread use of underwater vehicles is energy storage. Current lithium-based battery systems give  UUVs 3-day mission durations. After that, a ship must retrieve the UUV, recharge it, and redeploy it. Requiring a ship to be so heavily involved in UUV operations is expensive and defeats the purpose of unmanned operations. There exists a host of interesting missions that could be accomplished by UUVs that are out to sea for longer periods of time. For example, UUVs could be positioned near ports of interest for long periods to monitor submarine activity (a mission called "hold at risk").

Professor Doug Hart at MIT is working with MIT Lincoln Labs to develop technologies that would expand current underwater operation limits by 10x, or up to 30 days. He and his students have developed a number of working systems, including a diesel-powered hybrid system, an aluminum-gallium fuel cell, and an aluminum battery.

As a senior and master's student at MIT, I worked on a series of projects exploring, designing, and building multiple approaches to long-term underwater power sources for UUVs. I was a part of the first efforts in building longer-term power sources at MIT. I was on the engineering team that designed, built, and tested a diesel-powered hybrid system, as well as an aluminum-gallium system. My responsibilities included engine testing, vibration modeling and isolation, system integration, and fabrication.

In addition, I acted as the communications manager, maintaining all of the documents and reports to communicate and document our system for Lincoln Lab. I was also the project CFO, managing the $300k engineering development budget and parts procurement. This project helped to ignite my interest in business and management.

****

## <a id="robo-nav"></a> Indoor robot positioning and navigation

The internet of things is becoming a hot topic these days, and the promise of distributed sensory systems has broad applications. Some sensors measure data that could be modeled as a continuous field. For example, taxis (or Ubers) driving around a city could carry pollution sensors. If they report pollution levels, their location, and a timestamp, it would be possible to create a field, or "heatmap", of the intensity of pollution around a city over a period of time.

A graduate student at MIT was working on building an algorithm that could model a field based on intensity, location, and time. As a first prototype, he proposed using a small number of Roomba Create robots with light sensors. Inside of a dark room with one light bulb, these robots would drive around and report they intensity of the light and their location. This data would then be used by the algorithm to pinpoint the location of the lightbulb.

I designed a navigation system for the robots using MatLab. Since GPS is inaccurate indoors, I designed a system relying on visual tracking of the three robots to determine their absolute position in the room. I also programmed their navigation paths to ensure they were sufficiently exhaustive in collecting data around the room, and they didn't bump into each other.

****

## <a id="yo-yo"></a> Yo-yo manufacturing

One of the iconic classes for mechanical engineering at MIT is 2.008 (manufacturing). Students learn about a wide variety of manufacturing processes, the underlying physics that drive their efficacy, and theory for managing production lines. The best part of the semester, though, is designing a yo-yo and doing a 500-piece production run on MIT's injection molding machine.

Hoping to do something a little unique, my team settled on a yo-yo of a mouse running inside a wheel. The yo-yo itself was shaped like a hamster wheel (including rungs), and inside was a glow-in-the-dark mouse that spun on bearings. The idea was that when the yo-yo slept, the mouse would stay still while the yo-yo spun.

The yo-yo didn't really work out as hoped. In fact, it was kind of ugly. But it was an exciting opportunity to learn injection molding techniques. I was involved in every step of the process. We built solid models of our design and then created mold negatives, which we then CNC machined into aluminum. We used the injection molding machine to create the halves of the yo-yo and the mouse, and a thermoform for the window that went over the mouse. After the components were designed, we assembled and tested our yo-yos.

****

## <a id="gun-temps"></a> Temperature profiles of found firearms

When police are pursuing a suspect who has a firearm, the suspect will often try to dispose of the firearm, especially if they have prior convictions or are in a state with strict gun laws (like Massachusetts). The might throw it into a backyard or toss it in a garbage can. If the police can prove that the gun they found was the same one they say the suspect dispose of, they can build a case.

One way to demonstrate recent possession is to take a thermal image of the gun. If it was recently held by a suspect, for example in their hand or in their coat, it will be warmer than the surrounding environment. To support the strengthening of this type of evidence, I did a project modeling the heating and cooling of handguns. If the officers know the ambient temperature and the time since the suspect held the gun, they can use my model to show that it is very likely that the gun was recently held by the suspect.

I worked with the Boston Police Department to test the temperature profiles of several common handguns. I attached temperature sensors to several locations on the gun, and then charted the heating and cooling of the gun. I warmed the guns by holding them next to my body, and then cooled them by putting them in the ambient air (all of this was supervised).

I could use my temperature profiles and a semi-infinite heat transfer model to tell how long it had been since a gun had been held.
