---
layout: post
title: "Information Pioneers: A Conversation with Sandeep Rajput."
modified:
excerpt: "The Chief Data Scientist of Infosys discusses the importance of learning and listening."
comments: true
tags: [Infosys, Sandeep Rajput, Information Pioneers, Brad Allen, Stanford, databases, integration, data science, data, CS]
---

*Information Pioneers is a series I helped start in 2014 as part of [SDSI][1], the Stanford Data Science 
Initiative. The goal was to bring thought leaders to campus to help students learn from visionaries in
the data science field. It is currently hosted by the [INFORMS chapter][2] at Stanford.*

*[Sandeep Rajput][3] is the Chief Data Scientist at Infosys, as part of a long career in analytics and machine
learning.  This interview was given by me. Errors and omissions are my own, and any good stuff can be completely 
credited to Sandeep.*

<figure>
	<img src="/images/Sandeep_Brad.png">
	<figcaption>With Sandeep Rajput for Information Pioneers.</figcaption>
</figure>

## First things first, what does a Chief Data Scientist do? What does that mean?

I think it has three major components: one, providing advisory services to our clients who
want to explore what is "out there"; two, solving specific problems for them, eg, network
optimization, and; three, building a competency stream in-house, including appropriate training
programs. 

## In terms of the things you were doing at Microsoft and FICO - how did that give you the base to move into more advisory services?

In today's world, with the Internet making things so cheap to publish, everyone has an opinion.
But, if we look at some of the models I've built at FICO - they are still being used. They stand
the test of time. That gives me some credibility when working with clients.

## Would you mind talking about your PhD at Tennessee? How did that set you up for a career in data science?

The main reason I joined Tennessee's program was because the project was about non-linear dynamics
and chaos. It was applied in the sense that it was from a consortium of large chemical companies with a 
large set of signal data and wanted to apply statistical analysis to it, but weren't sure where to 
start. 

Over time, looking at things, it was like "ok, we are doing non-linear time series analysis." Today, 
this is called IoT, but it has been in research for a long time. We would do non-linear time series
analysis to say things like, "Hey, your furnace is going to conk out." In doing that, it became
more and more about pattern recognition. To determine if things were in the chaotic stage - which is
good, because one can do more with less, but it is higher risk. We were forced to look at the data,
because we couldn't extrapolate things. When you look at the data, you find all sorts of crazy things - 
values go to zero, they go to infinity, they are stretched. All of the common joys. This has been very 
similar to what I still see in the industry - data is floored, capped, amplified, cut short (in the 
sense of a third order hold). 

## You described FICO as "the oldest company alive that does nothing but analytics." Would you mind discussing a bit about FICO and how it helped you build a base for data science?

So, FICO has been doing analytics since the late 60s. They come up with an idea - that they would be
able to determine creditworthiness without using gender or race. It was a radical idea at the time,
but it slowly gained acceptance. A lab mate from my PhD days had left before me, and joined a company
which ultimately got bought by FICO. He called me and said, "Hey, we have got this data with all sorts
of interesting things happening. It's very complex. Are you interested? It has text data.." At that time,
60 bytes for merchant name and city was the extent of what text data represented. 

There was a lot we could do with the information, eg, answering questions like, "Where you buy?" and
"What you buy?"

## What were some of the things you were working on that led to a role at Microsoft? It sounds like a great job today - and very much of an outlier 14 years ago.

I think that's very true. Even now at FICO, we don't call these roles "data scientists." We call them 
"analytic scientists." To me, this is a good title - one works with a large amount of data. Models on
datasets would be 2GB. Which was a lot back then. Not today, but this is in the context of the 32-bit
architecture.

People know FICO mainly for their credit score. This might be a quarter of the business. This happens
once a month. FICO has other products also, like "Falcon Fraud Manager." It works on your payment card
authorizations. You as yourself, "How many credit card authorizations are posted?" or at least, "How
many are possible?" A very large number, in theory, is possible. Between one month and the next, someone
might have 10,000 transactions. In this sense, the solution must be quick - three minutes is too long.
30 ms is too long. We need to find a way to update the risk, and do it fast, and on a massive load.
70-80% of payment transactions go through FICO software now. Just to give a sense of the volume.

In moving to Microsoft, this experience was an important ingredient for them. Bing is a $2.5B advertising 
platform. If we improve this by even 1%, that is $25M dollars. So, I helped give guidance to advertisers 
on keywords, I helped guide engineers on growing the search systems. I worked on building the 
experimentation.

## How did you develop your background in these technologies, and how do you think about developing and balancing nascent technologies when creating the customer experience?

One of the things I did at Tennessee, was also get a Masters in Statistics. This helped me get credibility
on saying what constitutes a "good model." The lesson there for me was the role in continuing to learn.
Over time, cognitive dissonance has to fade. It's not "ML is good" or "ML is bad." One should just have
the flexibility to know when things are best used. And if possible, an eye towards shelf life is good. 

My role at Microsoft was officially in Product Management, which was a good thing. In the very beginning,
my team was looking at how money was flowing in. We could advise people, and even if we didn't implement
the recommendations, we could ask, "Well, what are you trying to do?" These are complex systems, with
whitelists and blacklists - and they are jerry-rigged. One looks at the metrics, and just knows what will
happen because it's been done before. We created confidence because we knew what we were saying. 
Regardless of algorithms, we could prove that we understood the business, and we understood what questions
needed to be addressed. 

## An additional skill that sits on top of technical competence is the ability to tell a story well. Bloomberg recently ran a story saying that "AI is the next frontier for Infosys." Would you mind describing your role in helping Infosys make that statement, as well as your role in helping create that story?

Infosys has 160,000 employees worldwide, and was the first $1B startup to come out of India. We do
systems integration and warehousing for business intelligence, and sit across many different industries.
For AI and Infosys, it means several things. We have clients who are unsure of the value of their
data. We have the credibility to help them discover this, in part due to our solid pedigree in technology.
Another interesting thing is that, change in large organizations is very difficult. Even Infosys is a
large company. When I came in, I said that we needed to move towards R - and it was a journey! People
use tools and hold dear value to them. Things are changing so rapidly that, every five years, people
have to educate themselves.

Even from an internal POV, that Infosys could be more agile and more aligned with what is taking place
in industry these days. The timescales are reducing. No one is going to do a $50MM, 6 year deal. They
will say - what can I learn from this data in the next 3 months. 

## Infosys made its backend on automation - doing systems integration to ease and improve workflow in a business. Now the work is in a sense, "automating" automation. To think of your role in a 160,000 person company as someone who helps provide that perspective. I'm hearing education come up frequently in your roles, both internally and externally. Would you mind talking a bit about your role as a listener in being able to do these things effectively?

Listening is the second most important thing I do in my job. The first, is, one needs to love looking 
at data. There is more science than data, in data science. But if one doesn't like playing around with
the information and spending four hours exploring data - then they will just cherry-pick what they want
to say. A model is meaningless if one doesn't know how to use it. I'll give an example to illustrate.

I was working with some otherwise bright people, who were building a machine learning model to understand
why customers had been spending a lot of money, and suddenly stopped. The model looked good. Accuracy
was 96%. Wow! We then find that the strongest predictor was the duration in which advertisers had not
been spending. Account managers - their jobs are to see if advertisers have spent - and they are already
making phone calls to folks who have not spent. So, the model is unusable. It doesn't change any habits.

Listening is so important. What if I go into Disney and use an SVM that classifies content as "family-
friendly" when it is actually pornography. They sell an experience - that is hugely brand damaging. Or
if I make a recommendation to Nordstrom that, if they discount, they will sell more. Nordstrom doesn't 
discount, except twice a year. Context matters. Making recommendations without context is like Dr. 
Strangelove sitting on the bomb going into oblivion. You just won't be heard from again. 

## How do you help others understand the need of the technology you're providing? How do you reach your audience at the level that helps them the most?

That is the hardest part. But if one truly loves their craft, they'll keep at it. There are asymmetries.
The customer expects some work. The title data scientist is funny to me - there is very little science that
can be done without data. I saw this on KDD nuggets: when I was in grad school, it was called pattern
recognition - but things continually get appropriated by the rung below. What a data scientist does
varies widely between people who say they are performing that work. 

We asked our folks: What skills are you looking for? What tools are useful? What are not? We'll then go and
ask our clients the same things. We came back with three types of roles: one is a data science engineer.
This role is most concerned about data at a very large volume. At a high level, they look at frequencies
and look at code that will deployed at scale. Another flavor is something we call a data science analyst.
This more like a business analyst role, and their focus is on communication. They will do many deductive
and translation activities with clients. The third is a data science "scientist." They are the ones who
look at the overarching approach. Even things like, "Do we even need to build a model?" 

Our perspective is that data science comprehensively can't be scaled. There have been fewer than 1,000 PhDs
in AI given out worldwide. However, we do think that data science engineers can be scaled - and that is
what we are focusing on as a company. This is the work we are doing with ICME at Stanford to help build
out this pipeline. 

<figure>
	<a href="https://vimeo.com/121107221" target="_blank"><img src="/images/Sandeep_Brad_Play.png"></a>
	<figcaption>Please click here to watch an original link of the video.</figcaption>
</figure>	


## Additional Questions:
* What in your view in data science do you think is a wide breakthrough that is worth working on?
* What makes a good data science team?

[1]: https://sdsi.stanford.edu/
[2]: http://web.stanford.edu/group/informs/cgi-bin/
[3]: http://sandeeprajput.com/