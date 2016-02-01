---
layout: post
title: Avoiding timeouts while web-scraping in Python
note: It can be frustrating when your scraping code stalls because the server isn't responding. Use this quick trick to keep things running smoothly.
---

### Painful server timeouts

I do a lot of web-scraping in my free time, and I am often pinging servers that aren't exactly the most robust. For example, when [scraping patents for patent valuation analysis](/patent-valuation), I am scraping the USPTO's patent database. It's an awesome system that is actually quite useful, but I found that every hundred patents or so, I would get a timeout on the server that would stall my code. Frequently, the timeout wouldn't resolve, so I would have to stop the code, hand-code a fix in the scraping loops, and restart. It was a pain, especially considering that I liked to run the code overnight given the large number of patents I was downloading.

### Frustration-free timeout handling

I knew that this had to stop, and that there has to be an easy way to keep code going in the face of timeouts.

Of course there is. I use Python's `requests` package to download webpages, and there is a handy exception that is thrown if a url takes too long to download. If you make the exception a part of a loop, you can get your code to keep trying to download a page until it actually works. It took me longer than it should have to find this sort of solution using Google and Python's documentation, so I want to share it in hopes that others have an easier time fixing their own problems.

 I've got the code below, but I've also [saved it as a Gist for easy reference](https://gist.github.com/winstonlarson/7dd141800227359a37ee#file-html-retry-py).

```python

import requests

timeout = 60 # How long to wait until trying again
url = 'http://winstonlarson.com'

while True: # Keep trying until the webpage successfully downloads
  try:
    page = requests.get(url, timeout=60)
    break # If it downloads, get out and get on with life
  except requests.exceptions.RequestException as e: # If it doesn't download after the timeout period, an exceptions is thrown, and we try again
    print('Try again')
    pass

```

This turned out to be the perfect fix. Often my program needed just one more try on the server and the page would download no problem. Your mileage may vary, but it's something to try.
