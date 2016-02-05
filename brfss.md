---
layout: page
title: BRFSS
---

Insights into health and behavior using data from the CDC

### BRFSS Introduction

Every year since 1984, the government has called around the country and asked people a series of probing questions about their health. As the largest and longest running health survey system in the world, the CDC's Behavioral Risk Factor Surveillance System (BRFSS) provides a wealth of information about health and health-related behaviors in the United States. It covers hundreds of variables over 400,000 adult interviews from all 50 states, the District of Columbia, and three territories. For more information about the survey itself, you should check out the [CDC BRFSS site](http://www.cdc.gov/brfss/).

The BRFSS is a rich source of information on how demographics, behaviors, and other risk factors can correlate with health. Many important population health studies and measures use the BRFSS as a key data source. For example, it is the source of the CDC's "Healthy Days" measurement, a key performance metric for the healthcare and health insurance industries.

Unfortunately, BRFSS data isn't exactly easy to deal with. Its breadth and structure have changed considerably over the years, and there are important sampling considerations that must be taken into account when using the data to draw conclusions. My goal is demonstrate how to use BRFSS data and some of the interesting correlations and associations that can be drawn from this data set using machine learning and statistical techniques.

The code for this project can be found on GitHub in my [BRFSS repo](https://github.com/winstonlarson/brfss).

### Getting BRFSS data

Anyone can download BRFSS data from the [BRFSS Annual Survey Data](http://www.cdc.gov/brfss/annual_data/annual_data.htm) page. There are links to each year the survey has been conducted. The data is available in `.XPT` (SAS Transport Format) or in `.ASCII` files. These are pretty big files, especially in more recent years. All together, the raw data is somewhere around 10GB.

The codebooks are available from the CDC for 1990-2014. I was able to find the codebooks for 1987-1989 from the [Washington State Department of Health](http://www.doh.wa.gov/DataandStatisticalReports/DataSystems/BehavioralRiskFactorSurveillanceSystemBRFSS/BRFSSQuestionnairesandCodebooks). The codebooks are availabe in my repo.

Python is my language of choice, and it's easiest to use the files in Python if they are converted into `.csv` format.  I haven't been able to find a robust solution for translating `.XPT` format data in Python, so I use an R script called `sas2csv.R` to conveniently translate the raw `.XPT` data to `.csv`. By the way, if you know of a nice way to deal directly with this data in Python, I'd love to hear from you.

The `.csv` files for the BRFSS are too big to host on GitHub, but I've made them publicly available on my [Amazon Cloud Drive BRFSS folder](https://www.amazon.com) to make it easier for everyone else to use them.

### Cleaning BRFSS data

Since cleaning a given year is a complicated and arduous process, I have detailed my methods for cleaning up an example year (2014) in [a blog post](/brfss-clean), which is also available as an [iPython notebook](https://github.com/winstonlarson/brfss/blob/master/clean_2014_notebook.ipynb).

A quick flip through the codebooks makes it clear that BRFSS data is not useful right out of the box. It takes some heavy-duty cleaning to get what you want. The codes and variable names can change subtly from year to year, so I had to check the codebook for every year of interest.

I started by grabbing and cleaning the basic demographic data available for each respondent. Not only did this process elucidate how to clean and use BRFSS data, but it's also useful in showing how the demographics of the survey change over time. I ended up grabbing the income group, race, state, age group, sex, and BMI of each respondent.

Due to the differences in codes over time, the easiest way for me to clean the data was to make a separate script for each year's data set. The scripts read in the entire data set for the year, grab the variables of interest, replace the codes with meaningful data, and save it back out in a standardized format as a `.csv`. The scripts for each year are in my GitHub repo.

Since all of the years now have clean tables that behave the same way, when I want to do analysis across multiple years, it's a much simpler exercise of reading back in the cleaned tables and easily examining my variables of interest.
