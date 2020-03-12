---
layout: post
title: "Information Pioneers: A Conversation with Julian Mann."
modified:
excerpt: "The cofounder of Skybox on the difference between a 'space' business and a 'data' business."
comments: true
tags: [Skybox, In-Q-Tel, satellite imaging, Information Pioneers, Google, Britt Jamison, Stanford, satellites, information, data science, data, CS, technology]
---

*Information Pioneers is a series I helped start in 2014 as part of [SDSI][1], the Stanford Data Science 
Initiative. The goal was to bring thought leaders to campus to help students learn from visionaries in
the data science field. It is currently hosted by the [INFORMS chapter][2] at Stanford.*

*[Julian Mann][3] is a cofounder of [Skybox Imaging][4], a satellite imagery company that was acquired by Google
in the summer of 2014 for $500 million. He is now an investor with [In-Q-Tel][5]. Julian was interviewed by my colleague 
Britt Jamison. Errors and omissions are my own, and any good stuff can be completely credited to them.*

<figure>
	<img src="/images/Julian_Britt.png">
	<figcaption>Britt and Julian for Information Pioneers.</figcaption>
</figure>

## So Julian, it wasn't that long ago you were in this exact classroom. Did you ever imagine you would be sitting in front of the class in 5 or 6 years?

We always believed we were going to be successful. It's a prerequisite for doing anything entrepreneurial, especially
for something as ludicrous and complex as what we did. In the aerospace terms, what we did were very fast. In Silicon
Valley terms, we were a bit of an ancient dinosaur.

## You mentioned a difference from other typical startups in the area. Can you tell us a bit about the idea?

The original idea behind Skybox came from some conversations with organizations that were interested in using
satellite imagery to change how they were doing business. One of the first was agro-forestry based carbon-offsets. They
were saying that they could verify projects were going on with the imagery; the problem was getting access to the data.
By analyzing the industry, we were finding billion dollar satellites being built and 80% of the capacity was going to
the US Government. This meant one customer was getting good service and everyone else was in the long tail. We were working
in a lab at Stanford making small, low cost satellites. We thought we could make satellites with good enough data, at 
a low enough price point, that would guarantee good quality of service to a large customer base. If you take that exact
statement and remove "satellite", it sounds like any other major disruption in history. We talked to a lot of investors
and many heard "satellites" and told us good luck. Some thought it sounded like the early days of semiconductors. It would
take a few million dollars to set up fabs and prove they are working - but once it does, it may be enough to change an
industry.

## Right, but it is difficult to set up a most viable product, a "MVP" for a system. How did you think about doing that?

So, MVPs as a model can be applied to complex systems. For us, we knew that we couldn't get enough money to get to launch.
Instead, we "rack and stacked" risk and be judicious about retiring risk in a quick and capital-efficient manner. We did
this through a few rounds of capital that ultimately ended up with a few satellites in orbit. 

## One of your investors said that it was the "riskiest investment" he made in 25 years. How did you think about trying to overcome them?

Risk in space, to us, was much more quantifiable risk than in other industries. One of the biggest point was in launch -
there is a 4-12% probability that the rocket will get to orbit. It is a significant probability, but it is also well understood.
So, you can plan for it, insure against it, and do many things. There are so many risks: operational, technical, market,
personnel, finance. We also had launch and regulatory risk. We felt like we could quantify them, and if we could retire them
quickly, that could be a competitive advantage for us going forward.

## What about experience? The industry is full of a lot of grey hair. There are not many young guys at the top. How did you think about starting and launching a company without having real day jobs?

Well, I was the sole one with just an internship. From early days, we talked a lot about engineering the DNA of the company.
In the very, very early days, we took all of our closest, smartest friends in the various disciplines we required. Once we
had that core brain trust of innovation, we said, "How do we get the right set of expertise - both within aerospace and 
outside of aerospace?" Our first camera systems person came from the medical device industry. The industry require high-
reliability electronics, they can't fail, and they were innovating faster than aerospace. 

## What was that early culture like, and how did you try to maintain it?

Especially in the early days of Skybox, it was very much managed chaos. It wasn't about hierarchy, and it was not about
experience. The best engineering answer always won, and it was very much a culture of "impassioned argument." That level
of passion and debate allowed us to have breakthrough innovations. Doing what others said "should be done" leads to the
traditional path in the industry of decade-long build cycles and tens of billions for satellites. 

## There are a few grey hairs of Skybox now, including the new CEO. He replaced a co-founder at an early stage. What was that like?

It is a difficult experience for any entrepreneur to go through. You are ceding a lot of control. As a founder, you have
some control and influence, but you are no longer "the one" in control. We knew we were doing something big, risky, and
complex, and we knew it was time. We were raising $70 million and we had to take the investors advice on what was required
to continue pursuing the vision. 

## Could you talk a bit about the vision of Skybox? What kind of company were you?

Even from the beginning, we never really viewed ourselves as a satellite company. We viewed ourselves as a data company.
This is for many reasons, one being that we would have never received investment as a satellite company. We were a data
company that just happened to have satellites in space. Our vision was about an unprecedented access to high-frequency
revisits to thousands of locations around Earth. One that would allow us to understand the global economy, global supply
chains, and the environment in ways that would tranform our understanding of the planet. Everyone wanted to contribute to this.

We had to backstop to a real plan that would make money, and that led to us joining selling imagery with this broader 
vision.

## Let's talk about that a bit. What were some of the applications you saw, of the data you would be bringing in?

We have a few canonical examples we have always thrown out. Cars in parking lots. Above ground oil storage containers with
floating roofs to understand their volume. This has a direct correlation to trading and getting ahead of earnings. It was
always my belief that the really transformative applications would not be conceived of ahead of time. Once we had the data,
and began to mine it and analyze it in ways that, up until a few years ago were computationally intractable, we would extract
insights about global behavior that we did not understand previously. This was difficult for us to point to big dollar 
opportunities in our vision. Luckily, we had investors that had the same confidence that we did as well. In parallel, there
was an existing ecosystem for selling pixels in a reasonably sized industry. It's a real business, with positive cash flow,
that provided returns to our investors. 

## You are talking about putting up satellites and "figuring it out." How do you design a company without knowing the applications yet?

We looked at it as a generic data infrastructure problem. We needed to be able to store massive quantities of pixel data,
we need to be able to analyze the entirety of that corpus of data, we need to be able to extract information from it. We need
to be able to analyze that extracted metadata, and we needed to close to the loop to take insights and go back to the pixel
space and keep the process going. We always had a vision of a data lake - we were adding data into the system that provides
more insights, creates new questions, and feeds the system.

## Can you talk about how your perspective is different than competitors and how that creates an advantage?

The traditional aerospace industry stores their imagery the same way that traditional enterprises stored their data 
15-20 years ago. The vast majority is stored on magnetic tape. They use big, expensive proprietary databases to store
their metadata index. They are stored in proprietary formats across a number of disparate systems for raw data, refined
data, extracted information - if there is even any. Ultimately, it is what you would expect if you went to an old
defense contractor and said, "Design us an information technology solution for storing tens of petabytes of imagery data."
The architecture is really great if you are collecting "X million square kilometers per day and storing Y million pixels
and maybe someone will analyze that someday, I don't really know." When you are looking at every new pixel and seeing
potential new information that can be derived, but only when analyzed in the context of all of the preceding information.
A new architecture is required, and ours was more akin to the perspective of a Google or a Facebook. 

## Let's talk about being acquired by Google. A $500 million exit in 5 years for satellites. It's great. How do you see your valuation in comparison to places like, WhatsApp, for example?

You are always going to see certain sectors for which you see valuations and scratch your heads. More power to these folks
who can do it. Some folks are going to end in hot water. Here's how I see it. Virgin America IPOed the other day for a little
under $1 billion. That means a company with over 100 jumbo jets has less than 2x the valuation of our startup with no
meaningful revenue to speak of. To me, what we have feels more appropriate for valuing a real business. 

## How do you feel about moving to Google? Now you are part of one of the biggest companies in the world.

It is a huge opportunity for us. We were saying we were a data company, but we had many more satellite engineers. The way
that Google asks us to think really is so much bigger than most are used to thinking. It is very much in line with what we
have always wanted to do. The part that is scary is now we actually have to deliver on this. Before, we were taking 
tiny deliberate steps to chase a grand vision. Google wants giant leaps. It's exciting and humbling at the same time.

## One of those leaps recently has been on [deep learning for image classification in Google Research][6]. Have you been interacting with that? 

One of the reasons we are so excited to be at Google, and that we believed Google was one of the only places that we 
could end up, is the depth of expertise in machine learning and computer vision. There are tremendous capabilities that
have been discussed publicly and there are many that are not discussed publicly. We are excited about what the future
holds for bringing the existing infrastructure to this novel data source.

## So what is the next thing for Skybox then?

We are building more satellites. We are launching another 15 in the next few years and going all in on the vision of
monitoring areas of interest and extracting information about the activity and behavior at those locations. I am really
excited to see what will happen when we get a lot of data flowing and the freedom to explore.

## What is the frequency and the volume of the data you expect to be creating? 

To us, daily monitoring is very interesting. It was always a question of frequency and spatial resolution. The highest
temporal frequency come from very low resolution systems. The [MODIS satellite][7] collects data at 200m resolution and is used
for atmospherics and weather modeling. There is a [Landsat system][8] that covers the Earth every 18 days at 20m resolution. Systems
that really allow us to understand large ecological changes, but nothing happening at a human scale. Looking at the market, 
1m resolution or better gives us customers willing to pay us. They will do it because we can see things happening at a human
scale. Being a bunch of engineers, we always brought it back to signal theory - what is the Nyquist sampling rate for that 
signal. For a lot of these, daily sampling gives a good ability to model activity and predict where things are headed.
More satellites will allow us get to daily monitoring and then scale the number of locations at which we can monitor daily.

## There have been many "space startups" recently. Do you think there is a space revolution now?

Again, we never really thought of ourselves as a space company. A lot of companies in this arena have different motivations
than we do. They are shoehorning businesses into space companies. I'm not sure that always ends well. There are a lot of 
pretty crazy ideas out there. For me, more interesting is a real business that just happens to require infrastructure that
operates in space. We happen to be at a very exciting point in time in which, the fact that the business happens to operate 
in space isn't a deal breaker. It actually is tractable that one can get their business going. If the same business can
be done without space - it is probably much more favorable path. Space is hard, expensive, the launch industry is completely
screwed up, there are many barriers. For us, we had no other way to go. It is tough, though, we have the scars to prove it.

<figure>
<a href="https://vimeo.com/114652664" target="_blank"><img src="/images/Julian_Britt_Play.png"></a>
	<figcaption>Please click here to watch an original link of the video.</figcaption>
</figure>

## Additional Q&A

* Has the federal government ever tried to intrude on what you are doing? 
* What makes you believe the value of the data justifies your valuation?
* In terms of flight software, what were the hurdles and has Google helped with that?
* Did your story evolve as you were raising money? Or were you specifically looking for someone whose vision matched yours?
* Could you walk us through a few of the challenges in getting your first satellite launched?
* What are some of the new opportunities that are created with more satellites in space?
* One of your competitors just had their whole fleet blow up on the platform. How did you insure
internally against risks like "time"?
* Who has access to your data in the future, and at what cost? What does this mean for privacy considerations?
* What were some of the low points, and what are some of the things you think you did really well?


[1]: https://sdsi.stanford.edu/
[2]: http://web.stanford.edu/group/informs/cgi-bin/
[3]: http://www.cnbc.com/2014/06/17/disruptors-in-2014-skybox-imaging.html
[4]: http://www.skyboximaging.com/
[5]: https://www.iqt.org/
[6]: http://googleresearch.blogspot.com/2014/09/building-deeper-understanding-of-images.html
[7]: http://modis.gsfc.nasa.gov/
[8]: http://landsat.gsfc.nasa.gov/