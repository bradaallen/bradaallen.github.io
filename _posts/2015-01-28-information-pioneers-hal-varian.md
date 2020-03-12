---
layout: post
title: "Information Pioneers: A Conversation with Hal Varian."
modified:
excerpt: "Google's Chief Economist talks about how data has shaped his life."
comments: true
tags: [Google, Hal Varian, Information Pioneers, Alistair Thornton, Stanford, economics, information, data science, data, CS, technology]
---

*Information Pioneers is a series I helped start in 2014 as part of [SDSI][1], the Stanford Data Science 
Initiative. The goal was to bring thought leaders to campus to help students learn from visionaries in
the data science field. It is currently hosted by the [INFORMS chapter][2] at Stanford.*

*[Hal Varian][3] is Google's Chief Economist and has long worked on the economics of technology. He is the founding
dean of the School of Information at Berkeley, and has influenced thousands of undergraduates with his books
[Intermediate Microeconomics][4] and [Information Rules][5]. This interview was given by Alistair Thornton. Errors and 
omissions are my own, and any good stuff can be completely credited to them.*

<figure>
	<img src="/images/Hal_Alastair.png">
	<figcaption>Hal and Alastair for Information Pioneers.</figcaption>
</figure>

## Today want to cover how Google uses data, and how they think about it. First question, how did that transition from academia to Google to take place and how was the transition?

Well, I was the Dean at Berkeley. I started the School of Information in 1995 and in 98-99 I wrote a book
"Information Rules" - it had several important concepts like network effects, switching costs, lock-in
and others. One of the fans of the book was Eric Schmidt. Deans get time off for good 
behavior and I wanted to try something different. Eric said, "Why don't you come
down and help us out?" They were all in one building, Building Zero. To preface the next
question, "What did I do?" Eric said, "Why don't you look at this ad auction and see if it
can make us some money?"

## How did you get involved in information? What sparked that?

My undergraduate degree was at MIT, and I spent a lot of time computer programming. At the
time, it was more of a hobby - well, if you're good at math you should be interested
in these things. I moved to Michigan, which interestingly enough, at the time ran the Internet.
They managed the NSF backbone, and I got interested in this - because I was trying to think about
what the economics of the Internet actually were (which changed dramatically over the next few years).
That was.. 1990, or something like that. Very early.

## How did you as a professional manage the transition from academia to Google? A place in which the incentives or the goals are so different.

Google is kind of like a University, but with money. Actually, Stanford is also kind of like
a University, but with money. The story then, obviously, was - in the spirit of inquiry and
research, and trying to work on interesting problems. Google was very visionary at that time, 
and still is. The biggest difference is, in academia, one can work on problems in months and
years. In business, that timescale changes to days and weeks. It was a lot of fun! We got to
explore and put some of the theories to work. I feel privileged to have had the opportunity
to work in both worlds.

## What exactly is a Chief Economist?

Eric asked me to look at at ad auctions. It was a well-developed area, and I was sure there
was a variation in literature that we could use - but it was actually quite different for Google.
It was designed by Eric Beach, who was an uber-engineer at Google, and Salar Kamanghar but 
it was primarily designed with engineering choices and I was able to add the economic context.

## Could you break this down for us? How does Google make money? And what is your role, in a data-driven context?

I like to say, I work on the dull side of Google. I work on the side that makes money. In this
case, Google makes money by selling ads. These ads are assigned to more prominent positions by
the bids that people make. There are a fair number of moving parts. Google was selling keyword
targeted ads, and the ads were priced based on a guess of what the value to the purchaser was.

We then realized we couldn't negotiate every deal we were making, and we saw a company GoTo that
structured their auctions differently. We used it as inspiration, and tried to improve it in several
ways. 

## Could you give us an example of how you would promote things using the ad auctions?

Things people get hung up on are the difference between a 'query' - which is what a user uses,
and a 'keyword', which is what the advertiser enters. How the two 'match' is a bit ambiguous.
It could be a synonym, an exact match, or a broad match, or a phrase match. There is a certain
amount of technology required to figure out what matches, and how the bids interact, and what 
the outcome is. 

## Within this context, what are some of the challenges for Google and advertisers?

Well, the responsibility of getting the match to work is for the advertiser. Google provides a
set of tools - for example, around the different types of matches - to help guide the bid process.
For example, "Jobs NOT Steve" for folks that are focused on employment. Nowadays, we have this
'entity search' which is nice. It allows us to do things like distinguish between wolverine as an
animal and Wolverine as a Michigan student. We can sense distinctions.

We moved from search ads, and then focused on contextual advertising. These are the things that
appear at the top of a box and might say "Ads by Google" with it. Its a similar idea. We moved
from there to purchasing DoubleClick and focusing on Display Ads. 

## Where is this evolving?

Nowadays, Google is looking at many different business models. Google Fiber, driverless cars,
the Android operating system. A lot of these things are complementary to our core services.
People say, "Why is Google doing driverless cars?" Well, we've got Google Maps, and then we have 
Street View - so there is a basis there. Sergey and Larry come to Stanford and talk with the 
autonomous team here, and realize there was a lot they could do to support the work on campus.
The context in those images helped develop that technology. 

## What are the challenges and opportunity you see at the heart of this "data machine" as it grows.

The folks who designed this system really needed to consider scale. We get more than 100 billion
queries a month at Google. You need the systems to handle that data, and then you say, "Hmm,
what are the capabilities we can do with this?"

## As an analyst, I found Google Trends so powerful. When I was living in Beijing, I would Google things like "China Hard Landing" to get a sense of sentiment around market crashes. This was a great, quick and dirty tool. How did you start to get interested in this? How did that come about?

In the early days, we started looking at the query volume on specific queries. And many of those patterns
were highly predictable. An example for me was "cruises." There is heavy seasonality to this. I thought,
we could share this with advertisers - so that they could understand query load and purchasing habits.

At the time this was very difficult to do - it was time consuming. So, we built out a product Google 
Trends to do this, almost instantaneously. A few years ago, I started matching this to economics. We 
had the recession. I would look at things like "file for unemployment" or "mortgage refinance." You can
imagine how important this would be over time and by geography. "Loan modification." A very big query
towards understanding stress in the mortgage market. It's been very interesting to extract this data
to predict economic activity.

## What do your interaction with policy, and how is this information being used?

Yeah, so it turns out. A minute ago, I said predicting. It's a very special kind of prediction. It's
predicting the present, not the future. We have all of these real-time information systems that let
one know what was happening in the last day, or hour - when the official government statistics come
out in a few months. Think of it as "nowcasting." Central banks are very interested in this.

Right, so when Obama's team came in in 2008. They were trying to build a stimulus package and dealing with
information that was 6 weeks old. Google isn't the only one who can help with this. Intuit has a small-
business employment index based on Quickbooks, LinkedIn has done stuff on most-rapidly going job 
categories. MasterCard can do spending by region, by retail store on a daily basis. This private sector
data is much more timely and up-to-date than what can be achieved in the public sector.

## What are some of the challenges in correlation vs. causation for Google flu trends? How do you think about issues related to that?

The correlation / causation thing is very intersting. We are doing very short-range, high-frequency 
predictions and are happy with correlations for that. For doing certain kinds of policy experiments or
the impact of advertising. The gold-standard for that is doing experiments. Something important for Google
is that very early on, they realized that we needed a robust system for experimentation and learning. For
example, trying something out with 1% of the population. 

There is this line, "You can decide something by looking at the data, or a HIPPO." (A Highly Paid
Person's Opinion) For causal inference, we believe strongly in experiments as a gold standard. The
story of Google Flu Trends is more mundane than the press might make seem. The two guys who put this together
have left. The team slowed down because the two founders/initiators had left. It was on auto-pilot.

The algorithms that had worked well in the first few years began to lose accuracy. The biggest issue
was that there was a positive feedback loop with the press. The press would say, "It's going to be a big
season" and people would Google **before** developing symptoms and the model would lose relevance
with regard to its predictive capabilities.

## How do you think about these feedback loops, and disaggregating real "core" search terms vs. maybe "secondary" search terms.

It's a real question. We think having more real-time economic data can help stabilize the system. That's
not necessarily obvious, though. Too rapid feedback could *destabilize* the system. There is a lot of
complexity in these feedback networks. There are many moving parts, and "what affects what" is pretty
tricky.

## The landscape of the use of data has changed quickly. What are the next big things you are looking at. When we had lunch, we talked about 'causal inference.'

What happens - I mentioned experiments are important. Sometimes, one can take observational data
and squeeze out causality. Economists have studied this a lot. We have developed some techniques that
are useful in other fields as well. In March, the National Academies of Science is having a meeting to
understand how to draw causal inference from big data.

## It's a hot thing at the moment.

It's a hot thing. Susan Athey and Guido Imbens are experts and very involved in this and thinking about
how it shows up in the big data context. Given my background, we have all been looking at the social
science background of this. It also shows up in genomics and other biological situations.

## What about careers? Most people here are unemployed, and at some point in their lives are going to need to find a job. What advice would you give to the students in the room? How do you think about hiring at Google?

I guess - people ask me about Google. Make sure you know a lot about Google before going. Things like
the breakdown of where the revenue comes from, and the ad auctions. The basic way the company functions.
This is good advice for anywhere you're looking, though. Then, in our area, "What kind of modeling would
you do for this phenomena?" We want to know how you approach problem solving. It's pretty hard to
prep for that, but it is the kind of thing you will often get at Google.

## You said "statisticians are a sexy job in the 21st Century." Tell me about that.

It's good to be complementary to something that is getting ubiquitous and cheap. This is happening for
data, but what is missing is the skill to take that and turn it into information, understanding, and
action. That is a skill that is definitely been very much in demand these days. A few years earlier was,
"How do you build these systems?" The private sector now is getting better at this, and the question is
becoming how to utilize this. 

<figure>
	<a href="https://vimeo.com/118299321" target="_blank"><img src="/images/Hal_Alastair_Play.png"></a>
	<figcaption>Please click here to watch an original link of the video.</figcaption>
</figure>

## Additional Q&A

* What is the interest in using Google's information for a hedge fund?
* How do you think about the antitrust allegations in Europe, vs. Google's place in the US? 
* Economic models are very rational - models that deal with large data sets are non-parsimonious
and it is more difficult to develop an intuition about the underlying trends taking place. What
do you think will give in the future as the two systems become more aligned?
* How successful do you think Google has been in its motto, "Don't be Evil"?
* Very early on in Google's history, Sergey Brin and Larry Page suggested a goal was to 'push
forward' AI. How successful would you say Google has been in doing this?
* How do you envision Google's relationship with blockchain technologies now and in the future?


[1]: https://sdsi.stanford.edu/
[2]: http://web.stanford.edu/group/informs/cgi-bin/
[3]: http://people.ischool.berkeley.edu/~hal/
[4]: http://www.amazon.com/Information-Rules-Strategic-Network-Economy/dp/087584863X/ref=sr_1_1?ie=UTF8&qid=1449512497&sr=8-1&keywords=hal+varian
[5]: http://www.amazon.com/Intermediate-Microeconomics-Modern-Approach-Ninth/dp/0393123960/ref=sr_1_2?ie=UTF8&qid=1449512418&sr=8-2&keywords=hal+varian