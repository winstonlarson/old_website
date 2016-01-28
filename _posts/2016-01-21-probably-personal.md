---
layout: post
title: Do I know you? Probably.
note: How Google Abacus' new probability-based identification system actually mimics the brain's concept of identity
---

Google made waves this week when it introduced [Project Abacus](http://9to5google.com/2015/05/29/smart-lock-passwords-is-cool-but-google-project-abacus-wants-to-eliminate-password-authentication/), a new prototype identification system for logging into Google's services. Instead of relying on passwords, Google proposes to use behavior to confirm a user's identity online. This feels like a pretty shocking idea: instead of using a binary confirmation of who we are (i.e. we know our password), Google basically wants to say that it's fairly certain that it thinks it knows who we are. However, this system of using probabilities to confirm identity is not only going to be more secure, it also actually mimics the way we humans think about identify ourselves.

### Increased security through Abacus

At first glance, not needing a password to log into your Gmail seems like a really bad idea. Can't anyone just walk in and use my Google account? The reality is that security experts hate passwords. There are a plethora of online services we use every day, and just as many passwords to remember. Most of us take shortcuts, using the same password over and over again or choosing a simple password. Both options are basically like leaving your front door unlocked. An increasingly important theme is in figuring out how can we solve the problem of passwords and find better ways to manage our online identities.

With Abacus, Google thinks it has the answer. Google proposes to expand the already massive amounts of personal data it collects on us and then use it to train artificial intelligence algorithms to know who we are. If you have a smartphone, it's not difficult to imagine collecting images, walking gait and speed, typing, app use habits, and a million other little data points. All of those data points will combine together to form a sort of profile. If our behavior continues to match our profile, Abacus can confirm that we are ourselves. If our behavior suddenly shifts in very unexpected ways, abacus can lock our accounts and demand a password (or some other fall-back system).

Sounds pretty great. No more passwords. I just do what I do and Google does the rest. Of course, this all assumes that you're okay with Google being Big Brother. There are plenty of privacy concerns: what else is Google using my walking gait data for? But that's another discussion for another post.

### A Bayesian approach to personality

So how does all of this work? Google is going to assign you a "trust score". The algorithm, and all of the types of data it includes, will of course be a trade secret. But the underlying mathematics of the algorithm will be rooted in Bayesian probability. It's a tool that gives mathematicians a way to be constantly updating an estimated probability based on new information that comes in as well as the old probability. If you want to know more about Bayes' theorem, [An Intuitive (and Short) Explanation of Bayes’ Theorem](http://betterexplained.com/articles/an-intuitive-and-short-explanation-of-bayes-theorem/) by Kalid Azad is an excellent resource.

Relying on Bayesian probability allows Google to take all of the disparate data types and boil them down into a single number that describes how likely it is that you are the person using your account. It's also adaptable. If you break your leg and all of a sudden your walking gait changes, it's okay. Your trust score will be affected, but probably not so much that you get locked out of your phone.

Contrast this with how a password works. If you know your password, Google believes 100% that it is you. If you don't know your password, Google believe 0% that it is you. With Abacus, based on your behavior, Google believes 80% that it is you, and that's good enough to let you into your account.

### Our brains are Bayesian, too

At first glance, Abacus can seem crazy. Why let someone access an account if you aren't 100% certain that it's them? Well, given our earlier discussion about the lack of security with passwords, you certainly can't use those to obtain 100% certainty about identity. But do you really want to let someone who matches only 80% into an account? Sure the math makes sense, but really?

This actually makes a lot of sense not only mathematically, but also intuitively. It's how your brain actually works with the people you know. Consider your friend Tom. You know your friend Tom because you know what he looks like, how he reacts in different situations, and that he's a nice guy and cool to hang around with. But if he all of a sudden started being the world's meanest dude, would he still really be your friend Tom? Sure, he looks like Tom, but he isn't really the Tom you know and love. Eventually, you'd probably stop being friends with Tom, mostly because he stopped being Tom.

Our perceptions of identity are the sum of our experiences with other people. When their behavior suddenly changes, those perceptions can become shaken, and our own behavior toward them changes. Hence the ever common, "That's not the good neighbor I know," after major crimes. Because it *isn't* the good neighbor we know.

Our brains basically have their own trust scores for all the people we know. As their behavior changes, those trust scores change (and hence our level of trust for that person) based on the new data our brains have been given. They're essentially endlessly computing a new bayesian probability for whether or not the person in front of us is someone we know.

### Our uncertain world

So while it may seem a bit wild at first, Abacus' probability-based identification system isn't so crazy after all. It is, in fact, working in much the same way as our own brains when we identify the people we know. It is a powerful paradigm for idenification. Whether or not we accept it remains to be seen.
