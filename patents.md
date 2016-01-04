---
layout: page
title: Patent valuation
---

***

##Valuing patents

Protectable intellectual property is a crucial piece of any corporate strategy for creating a long-term differentiated position in a market. Patents are a key part of IP strategy. Thanks to a series of high profile court cases, patents and patent strategy have become a highly visible part of technology strategy, representing billions of dollars in litigation every year. Patent valuation has arisen as a critical component of legal cases, startup valuations, and measuring R&D productivity.

There are many approaches to patent valuation, but a common and reliable method examines the number of patents citing a given patent (called “forward cites”). A patent with many forward cites is likely more valuable since it was the genesis of continued innovation. Theoretically, a highly cited patent is more likely to represent a company’s core technology, is more likely to be licensed, and will be more valuable in generating future IP. We can therefore measure a patent’s value relative to similar patents by comparing its number of forward cites with other patents in the same patent class.

###Counting forward cites

I created software that uses the USPTO website to find the find the information needed to value a patent. For a class of patents, I scrape the key information for each patent as well as its forward cites (i.e. patent number, title, abstract, assignee, and file date).

Given the large size of some patent classes and the large number of forward cites for mature patents, the code sometimes needed to run for days at a time in order to scrape the required patent data. With such a large data set and slow runtime, I had to take steps and devise a series of tricks to make sure that the code was robust and wouldn’t easily break. In addition, the range in the types of patents and the various bounds on searches (for example, certain classes during certain date ranges) demanded a fairly flexible and easily extended piece of software.

The code for this project can be found on GitHub in my [patents repo](https://github.com/winstonlarson/patents).

##Obtaining patent data

I relied on the [USPTO's advanced search website](http://patft.uspto.gov/netahtml/PTO/search-adv.htm) to scrape patent data, since existing patent databases are not flexible enough or too expensive to use for my purposes.

###Format of patent data
I had to scrape all of the patents in HTML format. I was looking for specific pieces of information that help to understand the context of the patent:

+ Patent number
+ Title
+ Abstract
+ Assignee
+ File date

###Scraping patents

I used python modules to download each patent. First, I had to create a search on the database and download all of the search pages in order to obtain the patent numbers in the class. Then I looped over the patent numbers and downloaded each patent's page in order to obtain the basic patent data I needed for valuation.

###Creating structured data

I used python's awesome `re` module for regex to get the data I wanted out of the HTML and then filter it into csv files (which ended up being huge).

##Building a complete solutions

I tied together each of the individual parts to create a full solution

###Creating robust software

I don't like it when things break. I had to play several tricks, including downloading all of the files locally, using HTML retries, and some fun regex tricks.
