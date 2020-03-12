---
layout: post
title: "Information Pioneers: A Conversation with Alon Halevy."
modified:
excerpt: "Google's Head of Structured Data on visualization and making information accessible."
comments: true
tags: [Google, Alon Halevy, Information Pioneers, Britt Jamison, Stanford, databases, integration, data science, data, CS]
---

*Information Pioneers is a series I helped start in 2014 as part of [SDSI][1], the Stanford Data Science 
Initiative. The goal was to bring thought leaders to campus to help students learn from visionaries in
the data science field. It is currently hosted by the [INFORMS chapter][2] at Stanford.*

*[Alon Halevy][3] is the Head of Structured Data at Google Research as part of a long career in databases.
He is frequently cited and has actually written ["the book"][4] on the topic. This interview was given by 
Britt Jamison. Errors and omissions are my own, and any good stuff can be completely credited to them.*

<figure>
	<img src="/images/Alon_Britt.png">
	<figcaption>Alon Halevy and Britt Jamison for Information Pioneers.</figcaption>
</figure>

## What does it mean to be Head of Structured Data at Google Research?

Well, first - it's great to be here at Stanford. It makes me feel 25, which takes me back about
10 years. What is structured data? Structured data is anything that fits into rows and columns.
If you think about Google, it is all about ranking and pages. Structured data is something we
were only thinking about three or four years ago. We have a research group that generates the
next set of technologies and features that will drive Google's search products. Structured Data
at Google is one of the biggest changes that has happened to web search in the recent past.

## How did you end up choosing to do your PhD here at Stanford?

Uh, they accepted me. It's obvious that computer science at Stanford is the best in the world.
And it was an honor to be a part of that. I wanted to solve artificial intelligence. In a PhD
you have about 5 years, that's enough time, right?

## You came to Stanford in the late 80s and early 90s. What was your interest in AI at the time? 

That's a good question. Well, I had a passion around 1990 (and still have that passion) regarding
getting the information one needs at the right time and the right place. This is before cell phones,
before the Internet, before all of that. This involves sifting through information, and understanding
what one is doing, and putting the two together. At the time, that was called "Knowledge Representation."
This was started here at Stanford by John McCarthy, who passed a few years ago but his work continues
here. 

## One joke for AI is that it is about "20 years away." And then 20 years will pass, and again it will be "about 20 years away." You were working on this 20 years ago, how has AI changed since then?

Uh, it has changed a lot. First of all, it works. It gives many services today that are valuable.
It is much more focused on machine learning. In mathematical logic, which was the school at the time -
something was either true or false. It didn't give us the opportunity to say anything "in-between" that.
The world is a bit more messy. The ML approach to AI allows things to be.. probably correct, or with
high likelihood. The user doesn't necessarily see that, but the system will give the highest ranked
option or make a decision from that. Machine Learning gives the system a bunch of examples of things
that do, or do not work, and then work from that. 

## So AI today is a lot about statistics, and programming. You focused most of your career on data integration and data management. How do you think about syncing those two perspectives?

Thank you for that question! I realized that I am not going to solve AI. This was before I was due
for a mid-life crisis. I was looking at a lot of information and trying to decide what is relevant to
a particular situation. I found in the world of databases - I can get stuff done. I can contribute
to products. Databases are boring. I found, to be effective, I actually had to take side courses in
stand-up comedy to be able to get the material to my students. This stuff is guaranteed to put you to
sleep, but it is very useful.

AI is taking data and reasoning about it. But, in the middle, there are systems and databases that are
doing very simple reasoning. They actually get you answers to questions you might be interested in. When
doing my PhD, I made the transition from AI to databases. And I found the most fascinating problem - I've
been spending my entire career trying to move away from this unsuccessfully because it is so fascinating. 
In every company you go, there is not one database. There are 50, 100, 1,000. No one cares about this 
problem - it's called schema heterogeneity. Heterogeneity is what makes life interesting, right?

So, data integration is that problem of trying to answer questions that stream data from multiple 
systems despite being created independently. The beautiful thing I realized about this as a professor
is that it guarantees you tenure. In the world of databases, it's the equivalent of AI - you'll never
solve it. You can always do more research and come up with great ideas. So, I got tenure. And then I
quit.

## In the last 10-15 minutes, we've probably said the word "data" 100 times. It's very buzzy. Why is it so important right now?

Probably because someone in the marketing department did a great job. The database community has been
dealing with "big data" for quite some time and now the New York Times is paying attention. That's a 
little cynical. There are many more systems that are collecting data about you - my car company actually
knows how I drive. And that can be shared with insurance companies, for example. Suddenly, this is 
something that is much more pervasive that can be brought to bear. There are risks with this, too.
Data integration and privacy don't go well together.

A second thing is an awareness of what can be done with data. Journalists are bringing data to bear
on things that people actually care about. A lot more people are seeing these effects and are interested
in the topics that are associated with it. Is "big data" really big? No, it's not much more different
than what was being done before. 

## The Guardian has used a product you helped create, Google's Fusion Tables. What was that experience like? Using an advanced data integration tool for a newspaper?   

The thing about databases is that they are the hardest software artifact to use. In order to really
work and tune a database, you need a lot of expertise. Some say, "It's easier to fly a 747 than to
tune a database. I think there some is truth in that." When I came to Google, I had big dreams. I wanted
to create a database that anyone could use. The interesting thing about database systems - the people
that have interesting data, don't care about databases. They actually have a life. They didn't take
my course at the University of Washington. But people care about what they have.

So, in 2009 we created Google Fusion Tables. I will quote Marissa Meyer, who once said, "If you launch
a product that you are not ashamed of, then you have waited too long." Thankfully, we were very ashamed,
but a lot of people use it. It's very easy. You upload a CSV, and with the GUI you can create maps and
make it beautiful and post it on your website. Simon Rogers, from the UK, loved this. Journalists have
a lot to say, and a lot of impact. One example was when Wikileaks leaked data about Afghanistan and Iraq.
This was in 2011 or 2012. This data was very well structured, and had a lot of geographic data. So we
tagged it to a globe. In one weekend, this had 100 million pageviews (!). Simon got an award for 
innovation in journalism and started giving tutorials about this. This is not big data, but it is 
a big number of eyeballs. For me, it's about the number of people who see the data and how it affects
their lives.

I know you're going to ask this question later, so I'll answer it now. The biggest challenge for "big
data" is making sure that we build tools to enable anyone with data to make sense of it. We can't hire
expensive database administrators. We need to get out of this bottleneck.

## There were a few powerful points we touched on there. One is making small data accessible. One that I don't want to be forgotten is, "releasing products to be ashamed of." What are some that you are most ashamed of.

Google Fusion Tables is one, definitely. It's gotten better now. Going back to journalists quickly,
if I can do that. This is another example of what happens when data gets free. In New York state, if
you ask for a permit to get a gun - it goes into a public database. This goes into a drawer in the
public library. A few years ago, journalists went to some county in NY and asked for this data with
the Freedom of Information Act. The journalists then went and geo-tagged it and put it online. You
can now see if your neighbor has a gun permit or not? This is really interesting, because "Do you want
to know if your neighbor has a gun permit?" Two days later, these journalists were harassed. But this
information was already public! They got harassed for making public information more public! This is 
creating questions we don't know how to answer.

## You're one of the foremost researchers on data integration issues probably in the world. I looked at Google Scholar and found, I think, 366 papers. One of those, is "The Infinite Emotions of Coffee." Could you talk more about that?

The book is written for folks with ADD. There is no connection between chapters. The connection to
data integration is loose, in that I was trying to "escape" data integration. I travel a lot for work,
and one of my first thing to do is visit a cafe. I started thinking about this - that there is a deep
relation between culture and coffee. And I decided to write a book about it. I started going to coffee
conferences. There were a few years in which I spent more time going to coffee conferences than
database conferences. You can guess which is more fun. Coffee is almost a "secular guide" to the world -
I learned a lot of history, I met some interesting people. I had small cups in huts in Ethiopia,
or towns in Iceland, or a tiny shop in Sarajevo. 

Work life balance is not about working less - it's about finding that other passion. Once it grabs you,
things will balance themselves well. This became my passion. I met a lot of folks, and every now and then
some high-falutin' bags of beans might drop by my door as a gift.

## How has your passion around coffee affected your professional life, if at all?

Well, it gives you a lot of humility. I would go to book publishers with my idea and they would say,
"That is a great idea! And, how are you thinking about doing something about data?" This was because I was
better known for that. I used coffee as a way to test Fusion Tables. Whenever there was a new feature,
my first use case would be coffee. It's just a nice way to test things. At Google, I'm known as
"the coffee guy" and in coffee, I'm known as "the Google guy." It's a nice balance.

## Let's talk about being a "Google guy." What's something you're currently working on that excites you?

Hm, this is recorded right? (laughter) One day, a few years ago - Have you ever seen an HTML table? 
Like on Wikipedia pages, the facts. That's data. It's a small database. Tiny - 200 rows, 4 columns -
but it is a database. One cool thing about Google is that you can write some small code and 2 hours
later you can have an answer. You can't do this anywhere else. I did this, and in English - there 
is something like 14 billion HTML tables. 99% of these are crap. But with that volume, there is 
something like 150 million tables.

The dream now becomes, "How do I make this information more accessible for others?" Now, when you
use Google and you query, the data from that table will present itself in your search results. That,
to me, was a journey that took like 7 years. It was a hard problem, but it was fun.

## Instead of "biggest challenge" - what would you say are some of the biggest needs in big data or data science?

The big needs are letting more people have the tools to analyze data. Even if we multiply the number
of students we teach at Universities in statistics and databases, we won't have enough people to
effectively make use of the information we are creating. So we need to reframe how we answer this question.
A second challenge to that is that the fields to do this well are somewhat disparate. One can get
a lot of value out of data, but one can also get a lot of bad information. Things can go wrong, and 
it is dangerous. The risk of a wrong conclusion. 

<figure>
	<a href="https://vimeo.com/117353977" target="_blank"><img src="/images/Alon_Britt_Play.png"></a>
	<figcaption>Please click here to watch an original link of the video.</figcaption>
</figure>


## Additional questions:
* How do you picture the world 20 or 50 years from now? With regard to the need for data scientists, for example.
* You came into Google to help structure data after work with unstructured data. What advice would
you give to folks starting businesses today - with regard to managing technical challenges?
* There is a lot of opportunity for reanalysis. What do you think provides trust in the system to
allow for efficient analysis?

[1]: https://sdsi.stanford.edu/
[2]: http://web.stanford.edu/group/informs/cgi-bin/
[3]: https://homes.cs.washington.edu/~alon/
[4]: http://www.amazon.com/Principles-Data-Integration-AnHai-Doan/dp/0124160441
