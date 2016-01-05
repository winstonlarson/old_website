---
layout: page
title: Portable controls experiments
---

***

##Hands-on engineering education

Hands-on education is a critical part of any STEM program. Studies are increasingly showing that a project-based hands-on program is critical to helping students maintaining interest and succeed in difficult math-based majors. [The New York Times has reported](http://www.nytimes.com/2011/11/06/education/edlife/why-science-majors-change-their-mind-its-just-so-darn-hard.html) that most students quickly lose interest in the abstraction and theory that is the basis of many introductory courses. However, project-based courses can help students tie together their theoretical understanding and real-world experience, driving them to engage with the theory on a deeper level and reach true understanding.

The essence of engineering is the ability to apply physical and mathematical knowledge in solving problems. To be successful in doing so, experience in using knowledge learned in the classroom is absolutely necessary in engineering instruction, making the laboratory a key element of education. Controls and mechatronics, in particular, require intuition and experience when solving problems. Students gain intuition through experimentation with and observation of real physical systems reacting to changes in the environment. They must be able to modify controller design and see the effects on the system. Students learn best when they work at their own pace and have opportunities to tinker.

Unfortunately, due to budget and staffing limits, it can be difficult to provide a good experiential environment for all students, especially in large undergraduate classes at large teaching universities. Controls experimentation in an educational setting is generally limited to being conducted in a well-equipped campus laboratory. Complex and expensive equipment are a barrier to entry, and include function generators, oscilloscopes, DAQ equipment, and the lab setups themselves. The need for equipment restricts experimentation time to assigned lab hours, limiting the possibilities for learning and experimentation.

For my senior thesis in mechanical engineering at MIT, I tried to solve this problem by developing a series of mechatronics and controls experiments for undergraduate classes. Dynamics and controls is a passion of mine, and I wanted to create tools that other students could use to discover the field. A copy of my [senior thesis](https://dspace.mit.edu/bitstream/handle/1721.1/74445/813303533-MIT.pdf?sequence=2) is available from DSpace@MIT.

##A portable controls laboratory

The ideal laboratory experience would be one in which the student could work outside of the laboratory, spending as much time as necessary to fully understand the lab work. In this approach, assigned lab times can be used to refine students' understanding of the material, or for helping students through difficulties. This more personalized and flexible approach would improve learning outcomes while leveraging valuable equipment and staff.

We built the experiments based on the myDAQ system, which is built by National Instruments. It makes it possible to take controls experimentation out of the laboratory, enabling students to conduct labs in their dormitories, libraries or any space with access to a computer. With appropriate software, the myDAQ may simultaneously act as a function generator, oscilloscope, and controller platform.

Our goal was to develop the hardware and software necessary to allow students to conduct controls experiments anywhere using portable equipment. Because of the unique nature of the myDAQ and the accompanying experiments developed by this project, we wrote reports documenting the hardware, software, and their use. Our reports explain the hardware and software setups, theoretical backgrounds on the plants and controllers, the equipment involved, and a user's guide to using the labs. They also include problem sets and laboratory work for the students to complete using the setup.

##Creating portable experiments

We developed two simple controls experiments for use with the myDAQ device. These experiments each fit on a single PCB which is approximately the size of the myDAQ itself and which can connect directly with the myDAQ I/O connector. The designs highlight the portability of this new lab setup. Everything the student needs for a complete controls lab experience weighs less than a pound and can fit in a gallon-sized ziplock bag.

###Experimental hardware

We designed two physical plant setups. First we studied a series of operational amplifiers which act as single or double integrators. Our setup provides a reference input as well as disturbance and noise inputs. We implement proportional, proportional- derivative, and proportional-integral control digitally through the myDAQ.

The second plant we developed was a voltage-controlled DC motor attached to a small rotational inertia. The controller acts as a cruise-control for the DC motor. As in the integrator experiment, we implemented proportional, proportional-integral, and proportional-integral-derivative control digitally through the myDAQ. The experiment board includes the DC motor, a motor driver, a battery, and a tachometer to measure the speed of the flywheel.

Both experiments each fit on a single PCB equipped with a connector which allows it to be plugged directly into the myDAQ. An emphasis was placed on keeping the experiments as simple as possible.

###Control software

We used Labview to develop a graphical user interface (GUI) interacting with the myDAQ and the plant for both experiments. The basic parts of the LabView programs were the same for both experiments, and we built:

1. **Function generator:** A function generator allows the user to choose the reference inputs into the system.
2. **Oscilloscope:** The oscilloscope allows the user to examine plots of the reference signal, con- trol effort, plant output, and other signals generated and measured in the ex- periment.
3. **Controllers:** Controllers use the error between the reference signal and the signal coming into the myDAQ from the plant to output a control effort back to the plant.

###Testing the setup

In order to guide experimental testing, we developed models of both systems with representative controllers. We chose a few representative systems confirm system behavior and detect unanticipated experimental behaviors. We derived the closed-loop transfer functions for each representative control system and plug in appropriate numerical values. We applied representative gain values to the systems, and we used MATLAB to predict the step responses and sinusoidal responses of the systems. We used the predictions to evaluate the experimental system designs.

We tested the experimental systems with the representative controllers and analyzed experimental system performance. We also observed irregularities in the hardware and software. While the op-amp system was reasonably well behaved, the DC motor system suffered from extreme sensor noise and sampling frequency problems. Hardware limitations including software time delays and low sampling frequencies, and sensor noise proved to be significant problems in building robust controls experiments.

###Laboratory write-ups

We produced write-ups to guide the use of the hardware and software developed in this project. Our write-ups can be used by instructors of controls courses to build laboratory programs which their students may follow. Much of the material is written such that it may be used directly by students in the lab. Also, our write-ups stand alone. An interested person with the necessary skills can use the lab and write-up for self-instruction. These reports were an important part of using the myDAQ system to make controls experimentation more accessible and available to broader audiences. As part of this, we wrote a series of pre-lab and lab problems based on the experiments. We hope that these pre-lab problems will prepare students for the experimental part of the lab, and will help them to contrast their predicted behaviors with how actual hardware behaves.
