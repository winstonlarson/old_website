---
layout: page
title: Patent valuation
---

## Valuing patents using forward cites

Protectable intellectual property is a crucial piece of any corporate strategy for creating a long-term differentiated position in a market. Patents are a key part of IP strategy. Thanks to a series of high profile court cases, patents and patent strategy have become a highly visible part of technology strategy, representing billions of dollars in litigation every year. Patent valuation has arisen as a critical component of legal cases, startup valuations, and measuring R&D productivity.

There are many approaches to patent valuation, but a common and reliable method examines the number of patents citing a given patent (called “forward cites”). A patent with many forward cites (some patents have hundreds of forward cites) is likely more valuable since it was the genesis of continued innovation. Theoretically, a highly cited patent is more likely to represent a company’s core technology, is more likely to be licensed, and will be more valuable in generating future IP. Patents are organized by class and sub-class, thereby grouping similar patents together (some classes contain hundreds of thousands of patents). We can therefore measure a patent’s value relative to similar patents by comparing its number of forward cites with other patents in the same patent class.

### Counting forward cites

I created software that uses the USPTO website to find the find the information needed to value a patent. For a class of patents, I scrape the key information for each patent as well as its forward cites (i.e. patent number, title, abstract, assignee, and file date). This involved leveraging the websites search format to find the desired patent classes, find all the patents in the class, and then download each patent's individual page. I then used regex in python to create structured tables out of the downloaded HTML files.

Basically, we needed a solution that could turn patent class and forward cite searches into structured tables that could be analyzed to understand comparative patent values.

Given the large size of some patent classes and the large number of forward cites for mature patents, the code sometimes needed to run for days at a time in order to scrape the required patent data. With such a large data set and slow runtime, I had to take steps and devise a series of tricks to make sure that the code was robust and wouldn’t easily break. In addition, the range in the types of patents and the various bounds on searches (for example, certain classes during given date ranges) demanded a fairly flexible approach. In addition, the frequently shifting goals and needs of the project that this effort was a part of also required an easily extended piece of software that could handle new requirements with minimal additional coding.

The code for this project can be found on GitHub in my [patents repo](https://github.com/winstonlarson/patents).

## Automating patent searches

I relied on the [USPTO's advanced search website](http://patft.uspto.gov/netahtml/PTO/search-adv.htm) (which I refer to as PATFT) to scrape patent data, since existing patent databases are not flexible enough or too expensive to use for my purposes.

### Scraping patents

The great thing about PATFT is that it has a very predictable format in translating searches into URLs, so it's easy to search for patents or patent classes using just URLs. This means that given a class number `classNum`, I can get the search results by using the URL `http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=0&p=1&f=S&l=50&Query=ccl%2F' + classNum + '&d=PTXT'`.

I used Python's `requests` package to grab the HTML pages for the class searches. After searching for a class, I needed to figure out how many patents were in the class, since search results are served on pages of 50. I could then loop through each search results page and grab all of the patent numbers in the class. After getting a list of patent numbers, I could then use a similarly standardized URL to search for the webpage for each patent, and I would again grab the HTML.

Finally, after getting information on all of the patents in a class, I completed a similar process for searching for, getting a list of, and downloading the webpages for each patent's forward cites. The PATFT search tools and URL formats were similar to before.

### Creating structured data

I had to scrape the webpages for all of the patents and forward cites in HTML format. I was looking for specific pieces of information that help to understand the context of the patent:

+ Patent number
+ Title
+ Abstract
+ Assignee
+ File date

I used Python's awesome `re` module for regex to extract this data out of the HTML files. I filtered the results into `csv` files (some of which ended up being absolutely enormous) in order to easily view and manipulate the data, with rows representing patents and columns the desired information. These data files were used to analyze patent values.

### Building a complete solution

I tied together each of the individual parts to create a full solution that is easy to use. I am able to enter the patent classes we would like to value, and the software generates the desired `csv` files of lists of patent and forward cite data. Controller files tie together the different functions for downloading different types of search results and then extracting the relevant data and producing structured files.

## Creating robust software

I have to admit that all of this sounds relatively simple:

+ Use standardized URL formats to complete patents searches
+ Download relevant HTML files
+ Use regex to get what you want out of the file
+ Save it to a `csv`

All in day's work, right?

Yeah, right.

The bulk of the code is built to deal with the problems and exceptions that arise out of irregularities in the PATFT system and database. A series of problems arose that I had to deal with, which wasn't easy given the large scale of patents that had to be processed.

+ The project needs changed frequently, requiring different pieces of the code be rerun or rebuilt, while leaving other pieces totally alone and unchanged
+ The PATFT server just loves to time out when loading webpages
+ The PATFT server is slow, and getting information on a class of patents can take a very long time
+ There are multiple types of patents and patent numbers, including utility and design patents, re-issues, and H documents. Sometimes patent numbers use commas, sometimes they don't
 + For whatever reason, the HTML formatting used in the webpages for each of these types of patents varies slightly
+ If a patent has only one forward cite, searching for that just brings up its webpage, instead of a results page
+ The code had to run on both Windows and Unix-based systems. Windows isn't fun.

To deal with changing needs and the long load times, I ended up downloading all of the search results and patent webpages locally. That meant that if an extra piece of information was deemed important, it was a matter of a couple of seconds to rerun the regex scripts, rather than a couple of days to re-download all of the pages again. It also meant that if the system stalled for some strange reason (like a computer battery dying), I could pick up downloading again from where I left off, rather than having to start all over again.

I used a [short bit of code](https://gist.github.com/winstonlarson/7dd141800227359a37ee) leveraging a little-known function in the `requests` package that retries downloading a webpage if it times out for too long. That ended up saving me a ton of headaches.

Dealing with the other issues was really a process of trial and error. Eventually, I ended up with a piece of software that I have used several times to do a series of different patent valuation projects, with minimal upgrades needed for new requirements due to the flexibility of the original code.
