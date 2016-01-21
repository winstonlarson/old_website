---
layout: page
title: Scientific advisory board membership
---

Access to world-class expertise is a core challenge for corporate R&D projects that are heavily dependent on cutting edge science. Generally speaking, the most advanced R&D projects are based in science that still lives in academic labs. Bringing top scientists and thinkers in-house is frequently not an option, since those individuals are on academic career paths, they are not interested in moving into industry, and the bulk of their research efforts (while very important) is too early for commercialization. To solve the expertise problem, many companies pursue a scientific advisory board (SAB) model, where they contract with top academics (also known as key opinion leaders, or KOLs) to provide their opinions on strategic research decisions. These engagements are usually less structured than full consulting engagements, and are centered on providing advice and guidance based on their research and specialized expertise.

The code and example lists for this project can be found on GitHub in my [authorship repo](https://github.com/winstonlarson/authorship).

##Publication records suggest scientific advisory board candidates

Identifying KOLs can be a surprisingly difficult challenge. The most well-known academics are often busy and over-scheduled, and it becomes necessary to cast a wider net. There are many well-qualified but less well-known or more junior scientists who can provide critical knowledge, offer new perspectives, and are often exploring new and non-traditional avenues that could prove to be highly successful. How can we identify exciting potential KOL talent?

A rudimentary way to measure scientific achievement is to examine scientific publication records. While there are many reasons why this isn’t perfect (for example, [Nobel Laureates tend to produce fewer papers](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0134164)), it is a good first order approximation, and examining publication records is a simple way to produce a list of potential KOLs.

The code and example lists for this project can be found on GitHub in my [authorship repo](https://github.com/winstonlarson/authorship).

###Obtaining topic-based scientific publication lists

We have to begin by finding a comprehensive list of scientific publications for the topic in which we we are interested. Obtaining a comprehensive list of publications can be surprisingly easy, especially in biology/medicine. The government’s [PubMed](http://www.ncbi.nlm.nih.gov/pubmed) citation database is a comprehensive collection of paper citations. After doing a topic search, they have made it very easy to download the full list of citations (often thousands of publications long) in a variety of formats.

As an example, we can look at prostate cancer. Using the PubMed database, we can search for “prostate cancer” and then download the entire list of 132,597 citations to a text file, as seen in the figure. There are a variety of other formats we could use (e.g. XML), but text ends up being the smallest file size and the easiest to work with.

<p align="center">
<img src="/images/2016-01-04-pubmed-results.png" alt="The pubmed website. Search for your topic, then click on Send to in the upper right corner." width="700">
</p>

###Using author metrics
We will identify potential candidates based on total authorship, first authorship, and last authorship. My method is based on a few high level assumptions.

1. **Total authorship:** The more you publish, the longer you’ve been in the field and the greater your expertise. The top publishers, however, will also tend to be the type of busy person that doesn’t have time to be on SABs.
2. **First authorship:** First authors led the actual research project that the paper is based on. This is usually the PhD student or postdoc who designed the experiments and wrote a lot of the paper. First authors tend to be junior to the last author.
3. **Last authorship:** Last authors are the leaders of the lab where the research was done. They usually act in a more advisory role and offer high level direction and guidance, rather than day-to-day grunge work. The top publishing labs will not only be led by the strongest senior researchers (last authors), but also tend to attract strong junior researchers (first authors)

Based on these assumptions, there are a few types of people that we might be looking for, based on needs:

+ **Heavy hitters:** Sometimes you really do want to get those top academics, even if they are busy. If you need guidance on a major decision and have the institutional prestige to attract them, you can probably get a couple hours of their time, although you will probably pay a lot for it. Look at the top of the total authorship list, as well as the top last authors, since they are leading the top labs in the field.
+ **New experts:** If you need expertise but not a lot of experience, you could rely on PhD students and post docs. They are frequently doing the footwork in experiments, and have the low-level knowledge needed to actually get work done using the newest methods. Their lack of experience also makes them much less expensive. Look for the top first authors, especially in the top labs.
+ **Rising stars:** For staffing a strong, longer-term SAB, you could look to junior faculty members. They are often doing exciting, cutting edge research, and are surprisingly knowledgeable, even if they haven’t built up the clout of more senior researchers. Look for top first authors in the top labs who have recently become last authors themselves, signifying that they were strong researchers who have just started their own labs.

These assumptions and guidelines are starting points. Having even a rudimentary understanding of the field and its leaders can be very helpful in interpreting the results of a publication analysis.

####Using Python and Pandas to create lists
The hardest part of this exercise was figuring out how to use the citation list to find interesting people. With that out of the way, we can get to the easy part: actually generating structured lists that we want from the unstructured text data.

I start by reading in the text document that contains the citation list, and I clean up the tabs and newlines. Prior to this, I’ve edited the text document by hand and deleted the first entries that didn’t actually have authors (since it was sorted by first author). I use regular expressions to grab the author list for each paper. I chop up the string, creating separate lists of authors, first authors, and last authors (all based on their position in the string).

Pandas makes it easy to play with my lists of authors. Using Pandas methods and list comprehensions, I can create lists of the top authors, top last authors, and top first authors. I can also create a list of the top first authors in the top labs.

Using these lists, I can use the guidelines I mentioned earlier to build a list of potential SAB candidates. I can then do some background research on them and begin reaching out to them.

####Future directions
The method I’ve developed, while rudimentary, is effective and suffices for its purpose in producing a list of potential SAB candidates. There are a few things I may tackle in the future that would make my method more robust.

+ **Disambiguating authors:** In a large field (like prostate cancer), there can be many authors who share names (i.e. to how many different authors does "Smith J” actually refer?) One way to do this is to look at the author’s institution. However, there are some complicating factors. Authors move between institutions. And there is a frustrating lack of consistency in listing institution names. MIT, Massachusetts Institute of Technology, and Mass. Inst. of Tech. all refer to the same place. Sometimes authors at the same university (which itself has several name variations) lead multiple labs. So while it’s a simple idea, it could be frustratingly difficult to implement in code. Maybe I’ll try to make it a machine learning example project.
+ **Improved search:** While PubMed is great, its search tools are honestly lack luster. It could be fun to use text analysis algorithms to get a better handle on which authors are most interesting based on their abstracts. It might also be possible to use machine learning to understand high level research directions in a given field.
