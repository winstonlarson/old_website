---
layout: page
title: Portfolio
---

Some coding and analysis projects of which I am particularly fond.

****

###BRFSS

The BRFSS is the largest health survey in the world. It is conducted by the CDC, and there are over 400,000 interviewees every year who answer hundreds of questions. Many important findings about population health, trends in behaviors, and demographic differences in health and disease outcomes originate in the data provided through the BRFSS. A wealth of interesting statistical and correlative findings are buried in the data, but unfortunately, the BRFSS can be difficult to work with due to archaic data storage techniques.

I have cleaned up all of the available BRFSS data sets (1984-2014) to make them easy to work with. I have also begun using various machine learning algorithms and statistical methods with the BRFSS results. These demonstrate the value of the data, as well as the difficulties inherent in health data and policy.


[Read more about my work on the BRFSS](/brfss)

****

###Patent valuation

Protectable intellectual property is a crucial piece of any corporate strategy for creating a long-term differentiated position in a market. Patent valuation has arisen as a critical component of legal cases, startup valuations, and measuring R&D productivity. There are many approaches to patent valuation, but a common method examines the number of patents citing a given patent (called “forward cites”). A patent with many forward cites is generally more valuable since it was likely the genesis of continued innovation. One can therefore measure a patent’s value relative to similar patents by comparing its number of forward cites with other patents in the same patent class.

I created software that uses the USPTO website to find the find the information needed to value a patent. For a given class of patents, I scrape the key information for each patent (i.e. patent number, title, abstract, assignee, and file date) as well as all of the forward cites for that class.

[Read more about my work on valuing patents](/patents)

****

###Venture portfolio simulation

Portfolios of venture-based companies are inherently fraught with risk. As part of a project to build a strategy for managing a portfolio of high-risk biotech ventures, I created a Monte Carlo simulation of the portfolio. My simulation accepted basic assumptions about the expected life-span of ventures, their chances of success, and their expected costs. Based on a desired number of successful ventures over 10 years, we used the simulation to estimate:

* The number of deals the portfolio managers would need to do
* The approximate number of ventures they would be managing at a given time
* The expected amount of investment needed
* The approximate headcount in the portfolio at a given time

My simulation helped to inform the portfolio managers in creating their strategy and setting expectations around the output of the portfolio.

[Read more about my work simulating a venture portfolio](/venture-simulation)
