---
layout: page
title: Portfolio
---

****

I've worked on a variety of projects that reflect my interests in data science, business and management, and mechanical engineering.

####Data science
+ [BRFSS:](#brfss) Extracting insights from the world's largest health survey, including data wrangling and machine learning
+ [Patent valuation:](#patents) Scraping the USPTO website and structuring data to estimate patent values
+ [Venture portfolio simulation:](#ventures) Monte Carlo simulation of a venture portfolio to guide investment and management strategy
+ [Scientific advisory board membership:](#sab) Using scientific publication records to identify potential SAB candidates

####Business and management
+ [Innosight experience:](#innosight) A variety of management and innovation consulting engagements focused on developing strategies to advance and commercialize cutting edge R&D

####Mechanical engineering
+ [Unmanned underwater vehicles and disruptive innovation:](#uuv) Demonstrating the financial and strategic value of unmanned underwater vehicles (UUVs) and how they are disrupting traditional naval power
+ [Portable controls experiments:](#portable) Developing a series of portable lab experiences for undergraduate mechatronics and controls courses
+ [Bio-mimetic underwater robotics:](#stingray) Designing, manufacturing, programming, and testing small under-actuated stingray and salamander robots

****

### <a id="brfss"></a> BRFSS

The BRFSS is the largest health survey in the world. It is conducted by the CDC, and there are over 400,000 interviewees every year who answer hundreds of questions. Many important findings about population health, trends in behaviors, and demographic differences in health and disease outcomes originate in the data provided through the BRFSS. A wealth of interesting statistical and correlative findings are buried in the data, but unfortunately, the BRFSS can be difficult to work with due to archaic data storage techniques.

I have cleaned up all of the available BRFSS data sets (1984-2014) to make them easy to work with. I have also begun using various machine learning algorithms and statistical methods with the BRFSS results. These demonstrate the value of the data, as well as the difficulties inherent in health data and policy.


[Read more about my work on the BRFSS](/brfss)

****

### <a id="patents"></a> Patent valuation

Protectable intellectual property is a crucial piece of any corporate strategy for creating a long-term differentiated position in a market. Patent valuation has arisen as a critical component of legal cases, startup valuations, and measuring R&D productivity. There are many approaches to patent valuation, but a common method examines the number of patents citing a given patent (called “forward cites”). A patent with many forward cites is generally more valuable since it was likely the genesis of continued innovation. One can therefore measure a patent’s value relative to similar patents by comparing its number of forward cites with other patents in the same patent class.

I created software that uses the USPTO website to find the find the information needed to value a patent. For a given class of patents, I scrape the key information for each patent (i.e. patent number, title, abstract, assignee, and file date) as well as all of the forward cites for that class. The data generated can then be used to compare patent values.

[Read more about my work on valuing patents](/patents)

****

### <a id="ventures"></a> Venture portfolio simulation

Portfolios of venture-based companies are inherently fraught with risk. As part of a project to build a strategy for managing a portfolio of high-risk biotech ventures, I created a Monte Carlo simulation of the portfolio. My simulation accepted basic assumptions about the expected life-span of ventures, their chances of success, and their expected costs. Based on a desired number of successful ventures over 10 years, we used the simulation to estimate:

* The number of deals the portfolio managers would need to do
* The approximate number of ventures they would be managing at a given time
* The expected amount of investment needed
* The approximate headcount in the portfolio at a given time

My simulation helped to inform the portfolio managers in creating their strategy and setting expectations around the output of the portfolio.

[Read more about my work on simulating a venture portfolio](/venture-simulation)

****

### <a id="sab"></a> Scientific advisory board membership

Accessing world-class expertise is critical for corporate R&D projects that are dependent on cutting edge science, but bringing top scientists in-house is often not an option. To solve the expertise problem, many companies use scientific advisory boards (SABs), where they contract with academics to provide advice. Identifying potential members can be  difficult since most well-known academics are extremely busy. Many well-qualified, although less well-known or more junior, scientists can provide critical knowledge. How can we quickly identify potential SAB members?

I developed a rudimentary method that relies on scientific publication records. I wrote a script that takes a full citation list for a given topic (e.g. prostate cancer) and identifies SAB candidates based on total authorship, first authorship, and last authorship. While quick and dirty, my method makes it easy to rapidly identify SAB candidates from a field of thousands, allowing the team to immediately begin making connections.

[Read more about my work selecting scientific advisory board candidates](/authorship)

****

### <a id="innosight"></a> Innovation and management consulting at Innosight

Translating new and exciting science into products and services that the market values is a key challenge in R&D-driven industries. Managing high-risk research programs and successfully commercializing ideas is difficult, but very worth it. Unfortunately, it is something that many companies (large and small) struggle to get right. Billions of dollars in R&D funds are squandered every year through mis-management. Understanding how to effectively run a R&D program and then commercialize the resulting products is a rare and valuable skill.

At Innosight, I have focused on advising and managing high-risk corporate R&D programs. I have built deep expertise in designing organizations and plans, communicating strategies to executives, and doing the legwork to get programs off the ground. On multiple projects ranging across a variety of industries, I have built a working knowledge of the underlying scientific and technological principles, engaged with scientists and engineers to test ideas, and created targeted strategies to build and sell products that people need.

[Read more about my work in R&D management at Innosight](/innosight)

****

### <a id="uuv"></a> Unmanned underwater vehicles and disruptive innovation in the Navy

Unmanned aerial drones have revolutionized warfare in the last decade. In many ways, they are a classic case of disruptive innovation, where small, inexpensive unmanned drones have replaced fighters and helicopters in carrying out dangerous attacks, fundamentally changing the way the Air Force operates. A similar phenomenon is occurring in the Navy. Small unmanned underwater vehicles (UUVs) are able to efficiently accomplish missions that would have previously required large, expensive shipborne operations. An important challenge in developing underwater vehicles is energy storage. MIT is developing technologies that would expand current underwater operation limits by 10x.

My master's thesis in mechanical engineering at MIT examined the financial and strategic implications of UUVs for the Navy. I found, for example, that the Navy could reduce costs by 95% by using UUVs for certain mission types. By not investing more in unmanned systems, the Navy is exposing itself to considerable financial and tactical risk.

[Read more about my work on UUVs and their implications](/uuvs)

****

### <a id="portable"></a> Portable controls experiments

Hands-on education is a critical part of any STEM program. Studies are increasingly showing that a project-based hands-on program is critical to helping students maintaining interest and succeed in difficult math-based majors. Unfortunately, due to budget and staffing limits, it can be difficult to provide a good experiential experience for all students, especially in large introductory classes.

For my senior thesis in mechanical engineering at MIT, I developed a series of mechatronics and controls experiments for undergraduate classes. Dynamics and controls is a passion of mine, and I wanted to create tools that other students could use to discover the field. My experiments, based on National Instruments DACs and Matlab Simulink, were small and portable, allowing students to take them home and tinker. That sort of hands-on tinkering is where true engineering learning happens.

[Read more about my work on portable controls experiments](/controls-experiments)

****

### <a id="stingray"></a> Bio-mimetic underwater robotics

As I have previously mentioned, underwater robots are becoming increasingly important to naval and maritime science operations. Robots must be robust and durable to survive in the harsh ocean environment, and many applications also require agility and speed. In the past, biomimetic underwater robots (e.g. robotic fish or stingrays) relied on segmented body designs, where each segment is individually actuated, to bestow agility and speed on their designs. Unfortunately, these segmented designs were not robust and suffer from high failure rates.

At MIT, I was part of a team that designed a bio-mimetic robotic stingray that solved these durability issues. It was constructed of a soft polymer body with only two actuators. I designed and demonstrated the control and actuation system to enable forward and backward motion and turning using only the two actuators. I also build and tested a robotic salamander that could both swim and walk.

[Read more about my work on bio-mimetic underwater robots](/biomimetic-robots)
