---
layout: page
title: Venture portfolio simulation
---

Managing a portfolio of venture-based companies is inherently fraught with risk. The oft-quoted statistic (that I can never find a proper citation for, oddly enough) is that only one in ten venture companies will succeed. Even fewer companies facing high scientific risk ever find success. Research-based ventures face particularly high risk, with long timelines and gigantic budgets between initial scientific insight and bringing a treatment to market. Creating a model that describes potential outcomes over the life of the portfolio can help managers to mitigate risk and communicate expectations.

The code for this project can be found on GitHub in my [venture-simulation repo](https://github.com/winstonlarson/venture_simulation).

##Simulating a research venture portfolio

As part of a project to build a strategy for managing a portfolio of high-risk research-based ventures, I created a Monte Carlo simulation of a venture portfolio. Based on the strategic structure of the portfolio, my simulation accepted basic assumptions about the expected life-span of ventures, their chances of success, and their expected costs. The managers knew that they desired a certain number of successful ventures over the life of the portfolio. To understand the effort involved in reaching success, we used the simulation to estimate:

* The number of deals the portfolio managers would need to do to bring ventures into the portfolio
* The approximate number of ventures they would be managing at a given time
* The expected amount of investment needed in total
* The approximate headcount in the portfolio at a given time
* and other useful portfolio metrics

My simulation helped to inform the portfolio managers in creating their portfolio strategy, setting and communicating expectations about the output of the portfolio, and the eventual amount of investment they might need to make.

###Venture portfolio strategy

The portfolio I simulated was part of the R&D arm of a large research-driven company. That meant that the goal of the venture portfolio was not to achieve some given return on an investment fund. Rather, the goal was to nurture high-risk research projects to a point where they could be adopted by the R&D group and developed into a full product. We designed a portfolio to help the managers identify interesting ideas and then test them out. If an idea was successful in meeting its first milestones with a little bit of money, it could set new goals and receive more money to achieve those. If the project failed to achieve its objectives, then at least they hadn’t spent that much money on it, and the idea could “fail gracefully” rather than languish in corporate limbo.

In essence, the portfolio became a kind of project pipeline or funnel (see the figure), where ideas would be initiated, and then move from stage to stage by achieving bigger and bigger objectives, receiving more money and headcount each time. This also meant, naturally, that there would be fewer projects in the more mature stages than there would be in earlier stages. Each stage of the pipeline had assumptions regarding the average investment, the headcount per project, the expected rate of success,  and the amount of time a project was expected to remain at that stage.

<p align="center">
<img src="/images/2015-12-10-img-funnel.png" alt="It was a funnel. With stuff in it." width="500">
</p>

###Why we needed a simulation

We knew how many projects we wanted at the end of ten years, but we needed to know what that meant for the actual operations of the portfolio. There were some important questions we needed to answer for the portfolio managers:

* How much money would the portfolio need each year?
* How many projects and ideas would they need to screen each year to reach their goals? What were the implications for considerations like hiring and lab space?
* How should they divide their time between different types of projects? How much time should they give to early-stage ideas vs. more mature, successful projects?

###Creating the simulation

There were several levels of information that I needed to keep track of in order to answer the managers’ questions. First, I needed to model a portfolio where the projects could be tracked. If projects failed anywhere in the pipeline, new projects needed to be started. As I mentioned, the portfolio was divided into stages, and each stage had a limited number of projects it could hold at a given time. Second, I also needed to keep track of the projects themselves. What stage were they at, what was their investment amount and headcount, how long had they been active, and were they successful at their current stage or failing? Third, I needed to track the progress of the portfolio each year. How much money was being spent, how many projects were active in each stage, and how many new projects would need to be launched?

I created an object-oriented system for keeping track of all these things. There is an `Accelerator` object that manages the portfolio and keeping track of time (since we were calling the venture portfolio an “Accelerator” in the spirit of start up accelerators), as well as the total amount that had been invested and the total number of successful and failed projects. The `Portfolio` holds the master portfolio and tracks projects. There are `Year` objects that keep track of the number of projects, budget, and headcount for each year. And then there are the projects, which are modeled as an object for each project at each stage of the pipeline (for example, I start with an object in the first stage. If that project is deemed successful, that object is deleted and an object in the subsequent stage is created). The Accelerator steps through years. Each year, budgets are calculated and projects are deemed successful or unsuccessful. Then the next year is initiated.

I had to start with some basic assumptions. I assumed that all projects were created equal. At each stage, projects had a given chance of success for that stage. They also had a standardized budget and headcount.

Finally, we started with some boundary conditions. We already had the first project in the portfolio, and a minimal headcount of portfolio managers, as well as a starting budget.

####Going to Monte Carlo
Since this is a Monte Carlo simulation, I determined the success of a given project in its stage by a random drawing based on the assumed success rate for that stage. Since the success of the projects was random, each Accelerator would be different. To understand the average expected behavior of the portfolio, I loop through thousands of Accelerator objects and take the average of their metrics (e.g. total budget).

The basic goal of the simulation was to understand what would be required to reach a certain number of successful projects that graduated from the portfolio. The key variable that we altered was the number of projects that could be brought into the first phase in a given year. Since it takes a certain amount of time for projects to move through all the stages and graduate, there comes a point when you don’t even want to accept new ideas anymore. If we knew that we wanted 3 successful projects over a 15 year timeline, we needed to know how many projects to accept in the earlier years to reach our goal.

To check that I actually set up this simulation correctly, I did a (fairly) simple binomial probability calculation. Let’s say that we would consider the portfolio to be successful if there were at least *k* = 3 projects that graduated by the end. If we set our simulation to accept a total of *n* = 30 new projects into our portfolio early on, and a project had a *p* = 18.75% chance of making it through all the stages successfully. The probability of the portfolio being successful (i.e. 3 or more successes) is

<p align="center">
<img src="/images/2015-12-10-math-prob.png" alt="P = \sum_{j=1}^{28} \frac{n!}{(2+j)!(n-(2+j))!}p^{2+j}(1-p)^{n-(2+j)}" width="400">
</p>

Which evaluates to about *P* = 0.59. That’s about the probability of success that the simulation predicted across many trials.

###Simulation results

As I mentioned at the beginning, the goal was to answer some key questions to help the portfolio managers understand and communicate the strategy and expectations for the venture portfolio they were running. A summary graphic is shown in the figure using dummy simulation data.

<p align="center">
<img src="/images/2015-12-10-img-graph.png" alt="A graph of the number of projects in each stage and the budget, over the time period 2015 to 2030" width="700">
</p>

I successfully used the portfolio to optimize the number of projects that they would need to bring into the portfolio in the early years in order to reach their goals by the end of the portfolio. I was also able to predict their expected budget each year, the number of projects they would be managing, and the headcount.

The Monte Carlo simulation was a key part of the business case to upper management for the venture portfolio, and it allowed the portfolio managers to better understand and communicate expectations for success and investment needs. The simulation provided critical data for designing the portfolio's operational plan.
