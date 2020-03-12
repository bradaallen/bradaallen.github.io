---
layout: post
title: "A Review of UW's Data Science at Scale course."
modified:
excerpt: "A challenging crash course in actionable DS concepts."
comments: true
tags: []
---

Over the past few months, I’ve been doing the [University of Washington’s Data Science at Scale course][1] on Coursera - a 4-course specialization that culminates in a capstone project for a certificate. The courses are meaty: they provide an “advanced beginner” instruction for performing data science: participants gain authentication to Twitter and pipe in data for analysis, compete on Kaggle, and set-up 20 instances on EC2 to Hive query a 0.5TB database. The capstone project involves an analysis of blight in Detroit that deals with all sorts of thorny causality questions.

For folks that might be thinking about doing the program, I wanted to share a bit of what a participant can expect to learn, some pros and cons, and things to consider when determining if it is right for you.

##Overview of Courses

The TL;DR version is that this course is highly recommended. Not only did I learn a lot; I felt like I was inspired to go learn things elsewhere. I had heard of Tufte’s work in visual graphics; I was fascinated to learn about a predecessor, Jacques Bertin, and his [work to develop a semiology of graphics][2]. Similarly, Bill Howe’s arguments for the benefits of reproducible research is one of the best concise arguments I’ve heard for centralized computing in organizations and the benefits of cloud services for managing large bandwidth swings. 

The four courses are: 

* *Data Manipulation at Scale:* This is a four week course that provides a crash course into relational algebra (as a basis for database structures); parallel systems / MapReduce; and the rise of NoSQL types, with a description of the more prominent types. In the first month alone, participants are also asked to do sentiment analysis on Twitterstream data, perform SQL queries, and program in MapReduce.
* *Practical Predictive Analytics:* This is a four week course that walks through different statistical philosophies (eg, Bayesian vs. Frequentist), common models, and different forms for how optimizations are calculated (eg, gradient descent). The course concludes with the participant choosing a Kaggle competition to complete and writing about the results. My write-up can be found [here][3].
* *Communicating Data Science Results:* This is a three week course that tackles some of the work that surrounds data science analysis: visualization and semiotics, privacy and ethics considerations, and reproducibility / cloud computing. The final project was both challenging and fun: spin up 20 EC2 instances and write Pig queries for a 0.5TB dataset. I had a lot of trouble viewing my jobs manager in Hue, etc. and frequently needed to get into the documentation to make sure I was looking at the right ports, etc. My write-up can be found [here][4].
* *Blight Analysis Capstone:* The capstone was a partnership with the City of Detroit to review some of their [Open Data][5] to try and predict houses that have blighted. It was a challenging data munging assignment; many of my data science exercises to date were relatively straightforward datasets. This required cleaning and joining a few datasets with records in the 100Ks. Ultimately, I learned a lot (including about geohashing :) ) and really enjoyed the work. My writeup of it can be found [here][6].

##Benefits

I hope the course overviews give a sense of whether this course works for one’s learning goals. It was very positive for me, for a few reasons:

* **Applicable Exercises:** I felt like I could understand *why* I was doing each exercise, and how it would help me professionally. For example, I won’t be programming in MapReduce anytime soon (I don’t think), but I did get a sense of how to think about the key-value relationship and changes I might make from a standard SQL syntax when working with a large dataset. Twitter, Kaggle, and AWS were all fun and well-known parts of the data science toolkit.
* **Well-Curated and Knowledgeable:** Bill Howe does a great job of articulating why these concepts are important *now*. He helps participant gain a sensitivity to “visual overload”, understand frameworks for manipulating data tables, and gives a sense of the underlying mechanics in scaled systems. 
* **Identifying “Where the Value Is”:** Because of the focus on developing an intuition with this technology, it becomes easier to get a sense of the problems that can be solved. It is not about being able to “do it” (although you learn that too); it is about giving context.
* **Inspired Additional Learning:** Similar to my preceding point, gaining context and intuition helps the participant assess what would be best to learn next. There are also references to concepts in privacy, ethics, visualization, etc. that the user can explore if interested.

##Challenges

Despite the fact that this course was good personally, that doesn’t mean it is for everyone. A few challenges I found:

* **The material is diverse and prohibitive.** As mentioned above, the assignments required coding with Python, R, Pig, SQL, and MapReduce. I spent a lot of time on StackOverflow and consulting my peers at SVDS. If I had been taking the courses without folks to ask for help, I’m not sure that I would have been able to finish the course. That being said, the average data scientist [uses 5 tools][7], so on the net this is probably a good thing. 
* **Some assignments need updated.** The best example of an assignment’s challenges was querying a dataset on AWS. I learned a lot about connecting to different ports, CLI querying, tunnelling, and calling ports to visualize jobs managers. Some of the ports in the instructions did not work for me - I had to go into the documentation and work with some Solution Architects at work to get the system set up correctly.
* **Limited responsiveness.** Most of the material for the course is from 2013, and has been selectively pruned since (for example, I think the section on graph databases has been added recently). I expected to start the capstone project immediately after finishing Course 3, but had to wait a few weeks. While waiting, I found *many* blog posts from people who had a similar issue and didn’t know when or if they were going to finish the specialization.

##So, who should take this course?

I would recommend this course for folks who are in organizations that have data science as a core part of their value proposition AND their role puts them close to that value creation. For example, a software engineer that is trying to gain more statistics experience, a data scientist that wants to gain greater insight into the engineering challenges of scaling, or a product manager. I might also recommend the course for academics (for example, PhDs in hard sciences) that might want to translate their skills to data science (this might be a useful onboarding experience before an [Insight fellowship][8]). I would not recommend this for people with a passing interest in data science, although it could be fun if you are up for a significant challenge!


[1]: https://www.coursera.org/specializations/data-science
[2]: http://www.amazon.com/Semiology-Graphics-Diagrams-Networks-Maps/dp/1589482611/ref=pd_sim_14_17?ie=UTF8&dpID=518z2BqNTDL&dpSrc=sims&preST=_AC_UL160_SR133%2C160_&refRID=010TD5VQHTZEATTGJQ6D
[3]: http://bradaallen.com/sf-opendata/
[4]: http://bradaallen.com/pig-querying/
[5]: https://data.detroitmi.gov/
[6]: http://bradaallen.com/blight-analytics/
[7]: http://www.kdnuggets.com/polls/2015/analytics-data-mining-data-science-software-used.html
[8]: http://insightdatascience.com/