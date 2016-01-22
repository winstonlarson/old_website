---
layout: page
title: Venture portfolio simulation
---

Managing a portfolio of venture-based companies is inherently fraught with risk. The oft-quoted statistic (that I can never find a proper citation for, oddly enough) is that only one in ten venture companies will succeed. Even fewer companies facing high scientific risk ever find success. Research-based ventures face particularly high risk, with long timelines and gigantic budgets between initial scientific insight and bringing a treatment to market. Creating a model that describes potential outcomes over the life of the portfolio can help managers to mitigate risk and communicate expectations.

The code for this project can be found on GitHub in my [venture-simulation repo](https://github.com/winstonlarson/venture_simulation).

##Simulating a research venture portfolio

I created a Monte Carlo simulation of a generalized venture portfolio. Based on a one potential strategic structure of a portfolio, my simulation accepts basic assumptions about the expected life-span of ventures, their chances of success, and their expected costs. My model assumes that a portfolio manager knows that they desire a certain number of successful ventures over the life of the portfolio. To understand the effort involved in reaching success, my simulation can be used to estimate:

* The number of deals the manager would need to do to bring ventures into the portfolio
* The approximate number of ventures they would be managing at a given time
* The expected amount of investment needed in total
* The approximate headcount in the portfolio at a given time
* and other useful portfolio metrics

My simulation is designed to inform portfolio managers in creating their portfolio strategy, setting and communicating expectations about the output of the portfolio, and the eventual amount of investment they might need to make.

###Venture portfolio strategy

Let's suppose that the R&D arm of a large research-driven corporation is interested in developing a venture portfolio. That might mean that the goal of the venture portfolio is not to achieve some given return on an investment fund. Rather, the goal is to nurture high-risk research projects to a point where they could be adopted by the R&D group and developed into a full product. Many corporations pursue this strategy. For example, one might think of Alphabet as a portfolio of very large ventures that are pursuing high-risk, high-reward projects.

In general, a portfolio can allow managers to identify interesting ideas and then test them out. If an idea is successful in meeting its first milestones with a little bit of money, it could set new goals and receive more money to achieve those. If the project failed to achieve its objectives, then at least the company hadn’t spent that much money on it, and the idea could “fail gracefully” rather than languish in corporate limbo.

In essence, a portfolio becomes a kind of project pipeline or funnel (see the figure), where ideas can be initiated and then move from stage to stage by achieving bigger and bigger objectives, receiving more money and headcount each time. This also means, naturally, that there will be fewer projects in the more mature stages than there would be in earlier stages (just like how there are more companies that raise series A funding than series B). It follows that each stage of the pipeline has assumptions regarding the average investment, the headcount per project, the expected rate of success, and the amount of time a project was expected to remain at that stage. These assumptions feed into my simulation.

<p align="center">
<img src="/images/2015-12-10-img-funnel.png" alt="It was a funnel. Divided into five stages." width="500">
</p>

###Why a simulation is useful

Let's suppose that a manager knows how many projects they want at the end of ten years, but they need to know what that means for the actual operations of their portfolio. There are some important questions they need answers to:

* How much money will the portfolio need each year?
* How many projects and ideas will they need to screen each year to reach their goals? What are the implications for considerations like hiring and lab space?
* How should they divide their time between different types of projects? How much time should they give to early-stage ideas vs. more mature, successful projects?

###Creating the simulation

There are several levels of information that I need to keep track of in order to answer these questions. First, I need to model a portfolio where the projects could be tracked. If projects fail anywhere in the pipeline, new projects need to be started. As I mentioned, one way to think about a portfolio is to divide it into stages. Each stage has a limited number of projects it could hold at a given time. Second, I need to keep track of the projects themselves. What stage are they at, what is their investment amount and headcount, how long have they been active, and are they successful at their current stage or are they failing? Third, I need to track the progress of the portfolio each year over the ten years. How much money is being spent, how many projects are active in each stage, and how many new projects will need to be launched?

I created an object-oriented system for keeping track of all these things. There is an `Accelerator` object that manages the portfolio and keeping track of time (since we were calling the venture portfolio an “Accelerator” in the spirit of start up accelerators), as well as the total amount that had been invested and the total number of successful and failed projects. The `Portfolio` holds the master portfolio and tracks projects. There are `Year` objects that keep track of the number of projects, budget, and headcount for each year. And then there are the projects, which are modeled as an object for each project at each stage of the pipeline (for example, I start with an object in the first stage. If that project is deemed successful, that object is deleted and an object in the subsequent stage is created). The Accelerator steps through years. Each year, budgets are calculated and projects are deemed successful or unsuccessful. Then the next year is initiated.

I had to start with some basic assumptions. I assumed that all projects were created equal (i.e. each is as likely as the others to succeed or fail). At each stage, projects have a given chance of success for that stage. They also have a standardized budget and headcount.

Finally, I thought it might be useful to get started with some boundary conditions that would probably prove realistic for a new portfolio manager. Let's support that there is already a first project in the portfolio, a minimal headcount of representing the early team, and a starting budget.

####Going to Monte Carlo
Since this is a Monte Carlo simulation, I determined the success of a given project in its stage by a random drawing based on the assumed success rate for that stage. Since the success of the projects was random, each Accelerator would be different. To understand the average expected behavior of the portfolio, I loop through thousands of Accelerator objects and take the average of their metrics (e.g. total budget).

The basic goal of the simulation was to understand what would be required to reach a certain number of successful projects that graduated from the portfolio. The key variable that I altered was the number of projects that could be brought into the first phase in a given year. Since it takes a certain amount of time for projects to move through all the stages and graduate, there comes a point when you don’t even want to accept new ideas anymore. It's like you were a VC that raised a fund. If you want to do a new round of projects, you go out and raise a new fund. So let's suppose that our portfolio manager knows that they want three successful projects over a 15 year timeline. They need to know how many projects to accept in the earlier years to reach their goal.

To check that I actually set up this simulation correctly, I did a fairly simple binomial probability calculation. Let’s say that the manager would consider the portfolio to be successful if there were at least *k* = 3 projects that graduated by the end. If we set our simulation to accept a total of *n* = 30 new projects into our portfolio early on, and a project had a *p* = 18.75% chance of making it through all the stages successfully. The probability of the portfolio being successful (i.e. 3 or more successes) is

<p align="center">
<img src="/images/2015-12-10-math-prob.png" alt="P = \sum_{j=1}^{28} \frac{n!}{(2+j)!(n-(2+j))!}p^{2+j}(1-p)^{n-(2+j)}" width="400">
</p>

Which evaluates to about *P* = 0.59. That’s about the probability of success that the simulation predicted across many trials.

###Simulation results

As I mentioned at the beginning, the goal here is to answer some key questions to help the portfolio managers understand and communicate their strategy and expectations for the venture portfolio they might be running. Visualizations are always helpful, so a summary graphic is shown in the figure using some dummy simulation data I generated using some of the assumptions I mentioned earlier.

<p align="center">
<img src="/images/2015-12-10-img-graph.png" alt="A graph of the number of projects in each stage and the budget, over the time period 2015 to 2030" width="700">
</p>

I can successfully use the portfolio to optimize the number of projects that someone would need to bring into their portfolio in the early years in order to reach their goals by the end of their portfolio timeline. I was also able to predict expected budget each year, the number of projects they could be managing, and the possible headcount.

My Monte Carlo simulation could play a role as part of a business case to upper management for a venture portfolio. It could allow portfolio managers to better understand and communicate expectations for success and investment needs. Hopefully, the simulation can provide critical data for designing a portfolio's operational plan.
