---
layout: post
title: "Information Pioneers: A Conversation with Arun Murthy & Tim Hall."
modified:
excerpt: "Hortonworks' Chief Architect and Head of PM share their philosophy on open source and changing paradigms around data."
comments: true
tags: [Hortonworks, Arun Murthy, Reza Zadeh, Information Pioneers, Brad Allen, Stanford, Tim Hall, information, data science, data, CS, technology]
---

*Information Pioneers is a series I helped start in 2014 as part of [SDSI][1], the Stanford Data Science 
Initiative. The goal was to bring thought leaders to campus to help students learn from visionaries in
the data science field. It is currently hosted by the [INFORMS chapter][2] at Stanford.*

*[Arun Murthy][3] is Hortonworks' Chief Architect and was part of the Yahoo team that developed Hadoop. He is a long-time
contributor to Apache and has served as a VP and Release Manager for ASF. [Tim Hall][4] is Hortonworks' Head of Product Management. I gave this 
interview with [Reza Zadeh][5], an expert on distributed computing and advisor to Spark pioneer, [Databricks][6]. Errors and omissions are my 
own, and any good stuff can be completely credited to them.*

<figure>
	<img src="/images/Arun_Brad.png">
	<figcaption>Brad, Reza, Arun, and Tim for Information Pioneers.</figcaption>
</figure>

## BA: So, Arun. "Chief Architect." That sounds like a very cool title, and something to aspire to. What does that mean on a day to day basis?

AM: Well, at a startup everything changes. From taking out the trash to setting up the chairs and tables. It's been an incredible journey.
Now, I run large parts of engineering and talk to customers. I have the pleasure of talking to a lot of them. It's a lot of travel. Getting
to discuss our solution with banks and healthcare companies - helping them see how much of an asset Hadoop and data can before their 
enterprises. It is a little scary how little these agencies know about their businesses, with regard to data.

It's been, frankly, an incredible ride. When we started back in 2006, we set up a few nodes. And they were crashing most of the time. When I
left Yahoo to start Hortonworks in 2011, we had nearly 50,000 nodes of Hadoop. Every dollar, to a large extent, that Yahoo, or LinkedIn, or
Facebook made has touched Hadoop in some way.

I've been trying to do open source for a long time. Way back in 2005, I used to work on PHP with [Rasmus][7] (the "father" of PHP) and that led 
to me having discussions to work at Facebook. I'm saying this because open source is a great way to create a brand for yourself and it's a 
great way to stand out. This is needed if you want to be technical. It creates this notion of a technical athlete. Folks at Google have done 
some cool stuff, but to some extent it stays within the walls of Google. Open source helps democratize you as an individual.

## RZ: That's a great segue to open source. At Google, there may be 20,000 to 30,000 engineers there and those relationships are important. You are also getting paid to code, which is difficult to do sometimes with open source. How do you think about making open source projects commercially viable, and why would you do that in the first place? Aren't there other incentive schemes to champion developers and support their careers?

AM: Let's take a step back and look at Yahoo's reasons for opening up Hadoop. Circumstances matter. Google was very far ahead of the pack in 2006,
and it was in the interests of Yahoo, Facebook, and LinkedIn to work together to build technology that is large enough to make an impact. Before this,
I had also helped contribute to Linux and PHP and other open source projects. In terms of incentives, Google's investment into MapReduce
and HDFS made sense at the time - but it didn't make sense for Facebook or LinkedIn. I now know people have worked at Facebook for 10 years. Open 
source is completely meritocratic. Your code speaks for itself and the cream rises to the top, and it puts you on the radar for a lot of people. 
I have known folks on Sand Hill Road for a lot of time, because of Hadoop. 

## BA: Strategically then, how does being open source have an effect on how products are brought to market?

TH: People ask me all of the time, "What does it mean to be a Product Manager in an open sourced company?" We are effectively working in a community that
we don't control. As a commercial entity, we are capitalizing on the ecosystem. If you look at major commercial software vendors and what they have
to invest in R&D (Google, Oracle, HP, etc), it takes a tremendous amount of money to get things off the ground. The open source model allows you to
attract smaller investments from really smart people, like Arun, and their collaborators to contribute to a single goal and objective. Each group gets
something unique and different, though - Facebook, LinkedIn, all use it in different ways. Together, all the boats rise a little big higher. By Yahoo
unleashing this intellectual property, they felt they would get benefits and contributions that would drive their business forward. Hadoop Summit in its
first year was ~200 people. Last year, it was 3,800 people in just a few years. 

So now, what do we do? Our job is about listening to customers, and how they want to use the technology, and our partners, and their requirements. We then
feed that back to Arun and use that to shape priorities, understand what is viable technically, and help make the platform progress.

## BA: That's fascinating. It's very interesting in the sense that traditionally PMs help generate the requirements. But for Hortonworks, the requirements are generated by a community, and its a much more public exercise to prioritize these for internal work. It's a spin on the normal dynamic.

TH: There is sort of a spectrum. There are things that Arun and I get to direct the engineering talent we have internally. There are other things we want help on.
So, we'll take the requirements and if we do not have the expertise or we want guidance, we'll put that out into the community. Other things, won't fall into
our priorities but we find them interesting, so we will share that with the community as well and see if folks jump on it. As a result, those things come back
into the platform for free. 

AM: The one major difference working for an open sourced company, as opposed to an Oracle or SAP, for example, is that we have the ability to influence and pull
interest and development from a broader pool of technologists.

## RZ: That can be a double-edged sword, right? As a PM, the priorities will be different across the companies in an open sourced ecosystem. This can be very challenging from the perspective of HR and, in particular, development time. How can you productively put in the features you need without the nuclear option of forking the project off on your own?

TH: It ends up being more of a communication challenge than a human resource challenge. We often get asked questions about roadmap: "What's coming next, and when
is it coming?" We have to deal with variability, because the community may not finish a project when we expect it, or they may have different priorities.

AM: At the end of the day, in open source, one can't control their destiny if they can't contribute. We as a public company have commitments on what we have 
to deliver. We put our money where our mouth is by putting people towards the priorities we want to ship. Hopefully that also aligns well with the needs
of other large technology companies. And then anything on top of that for us, is gravy. There may be conflicts in priority but, as Tim said, that's more of a
communication challenge. It comes down to the meritocracy of the space.

Of course, like any roadmap, as we get closer to delivery dates we have a better sense of the shape of the project. There are always surprises, though. There were
features committed in Hadoop 2.6 that, from a code perspective, came late in the game. This variability matters: even if there is a feature we don't care about,
it may have a negative interaction with a feature we do care about, or have an effect on the stability of the system. 

## RZ: That gets to my last question. There must be features that have implications for business opportunities for clients. How do you manage the satisfaction of clients with this variability? Are there situations in which more is required than just effective communication?

AM: Let me give an example for Hadoop. I am the Release Manager for Apache Hadoop, so I take responsibility for shipping in the community. How we do this is pretty
straightforward. We say, "This is the release target for 2.32, we think we can do it in 3 months, and these are the associated features." We'll go out into the
community and get feedback and have a negotiation process. Open source is just as much an art as a science. Because of this negotiation, experience and track
record matters, because it helps create trust in the process. Surprises do happen, though. For v2.6, we had a bunch of folks from Microsoft Research contribute
on a great feature. It was about up-front reservations and resource management. For example, "I know at 2am I will have a bunch of ETL applications show up, so
I want some resources reserved in the cluster to meet an SLA." It sounds like a cool feature, but it came in late and we found a bunch of bugs. We have to go deal
with it. We are careful to never fork. It's always an easy option, but two months later you end up in a place where there is no coming back. Once it gets shipped to
a customer, changes take place and its tough to move. It's better off sticking to open source, and dealing with the issues as they come.

## BA: The relationship between agenda setting and the constraints of being a public company sounds tough. For your customers, how do you think about things like the need for increased security - and how you're able to get that on the agenda and product development?

TH: In terms of our investments and IP, we think in 3 parts. First, the base that is organic. This was the original investment from Yahoo and the folks who came with
that project. That is what we've always done. The other models we are trying to invest in that may be less understood. 

Security is the second model. We bought a commercial closed-source company and then gave away their IP. According to auditors, this is "goodwill." 
We gave the IP to the Apache Software Foundation. You do this by creating an incubator proposal for a new project, and take the code as the initial 
"investment" into that project. We spoke to several parties we felt would be intersted in contributing on an ongoing basis, and now we nurture that 
community. Why did we do this? We saw the challenge in driving and accelerating individual investments across 20 or so open sourced projects, and we 
saw this company doing great work on a top down approach for centralized administration of security policy that also touched many of the most critical 
components of these other projects. This is called Apache Ranger. It's original name was Argus, who was the "Watchmen of the Gods" in Greek mythology. 
He was turned into the feather of a peacock, and we thought it would be cool as a part of the other products in the Apache ecosystem. But Apache flunked 
the name on trademark infringement, and we're stuck with Ranger. Our engineers tried for "Chuck Norris" as well, but that didn't work.

The third aspect of the model is what we've done in the last 3 weeks. Arun and I have been on a mini-roadshow to find interested development partners. We went to our
customers and asked "What are the most critical areas you're struggling with?" They said, "compliance." It may sound boring, but in the world of Enterprise IT there
are tons and tons of things that need to be complied with, such as Personally Identifiable Information (PII). These things are top of mind. As companies land more and
more data into data lakes, backed by Hadoop, the challenge is either around organization or compliance. For example, Basel III or SOX. There has been more regulation in
banking in the last four years, than the preceding 25. So, how does an enterprise deal with this? We went to interested companies and asked them to partner with us
in the open sourced community to work on projects that help deliver on compliance. This co-development effort we created with Target, Merck, Aetna, and SAS. It's
called the [Data Governance Initiative][8], and we launched it in December 2014. The idea is that we have engineers in each of these companies contributing to a new
incubator proposal that we'll marshal into Apache. They are working on the technical proof of concept for governance at scale, in Hadoop. The companies get a range
of things from this. They get to show they are innovative, and first-mover advantage. Also, from a business standpoint, they get more control over the requirements
and product definition. They also get to see the product on a daily basis.

## RZ: A segue into speed and quality of open sourced software vs. in-house. In the case of security, how is it clear that it should be an open standard? Are there governing principles that might lead it to be developed in-house and then released?

AM: Look, we are in Silicon Valley and the hardest thing to find is talent. If you are one company and you have the talent to build this then go for it. This was not
the case in the past for a Yahoo, LinkedIn, Facebook, and it is certainly not the case for Aetna, Merck, or a Target. Open source creates a level playing field
for these projects. Kudos to Google for being able to do it. In the 90s, Microsoft could do it and they can't now. It's an open question that Google will be able 
to do it in 20 years.

## BA: With regard to leveraging resources - much of the basis for this technology is for consumer-oriented projects. In shifting to enterprise, which is important for Hortonworks, there is a natural need for security. How do you see the paradigm shift between the relationship of code and data taking place? And the relationships of all three?

TH: This is Arun's analogy that I stole. In the late 90s and early 2000s, it was all about "the code." From an enterprise perspective, it was about writing and managing
applications, and the data were a byproduct. They were living in Oracle and SQL Servers or other commercial database projects, and it was finite. 
It was all about deploying apps on top of datasets. What is clear now, is that the center of gravity has shifted from code to data. The data is landing and has to 
be managed and monitored at scale and the applications are more transient. No one is trying to do vast quantities of data movement, because it is expensive and
takes time. One will write an algorithm that tries to extract meaning and insight from a dataset, maximize business advantage from that, and move on. The algorithm
may not be used again. To us, that is a big shift from the last century to this century.

AM: It's also about volume of data. Moving customers, moving a petabyte of data takes time because it is bumping up laws of physics. It takes time, and a lot of people
have a lot more than a petabyte of data.

## BA: As we are going through security, governance, and compliance concerns that these enterprise companies have, I am curious if you could talk a bit about some of the applications that customers like Aetna might use that would justify the value in making the shift to data lakes, Hadoop, and other technologies.

TH: There are two dynamics going on. The first is cost. The cost to store and maintain access data in a timely fashion is a big factor. Paying Oracle or Microsoft or
other major database vendors to store a petabyte of data is significantly more expensive with their commercial offerings than to store in Hadoop. 
You'll see companies trying to hold onto larger and larger datasets because of trend analysis and other statistics that can extract insight. One of our social media
customers was ingesting 15 TB a month in commercial databases. Because of cost, they were forced to dump a bunch of data on a monthly basis. However, the PMs
were having difficulty doing trend analysis and developing the algorithms that would help create effective ad placements because they weren't able to keep the 
supporting data to do meaningful analytics. So, they swapped out the entire database infrastructure for HDP using HBASE as the front-end serving store, then writing
it into HDFS and writing the analytics on top of that. 

AM: In terms of processing store, a large web company I know would run a single SQL query on a commercial database and would get a response in 32 days. This was in 2007.
Now they are running this on Hadoop and the response comes in 16 hours. Imagine the impact that this has on your business, and a lot of the improvements are architectural. We now
work with a retail company who would do clearance price analytics, and it would take 7 days to come back with a response. Today, on Hadoop, the response comes in
6 hours. It is changing their business to an unimaginably large extent. They can now actually do analytics that take into account today's weather. This has an 
effect on supply chain management. They can also look at larger data sets. Before, it was 30 days - now looking at 24 month trends are feasible. Or, they can increase
the fidelity of their analysis and look at changes on an hourly basis. Being able to see these changes, from the perspective of Hadoop, has been a privilege.

## RZ: Compared to Cloudera, how do you see the two businesses as being strategically different?

AM: From a technical perspective, it is very easy. Everything we do is open source. There is not a line of code we write that is constrained in the walls of our
company. It removes the friction of having to make a decision of whether to open- or close- our project. This also removes friction externally. Our customers
are never worried about saying, "If I go all-in on Hadoop, which is the first big change in architecture they are making since the database itself, what am I
going to do if this doesn't work?" Being open source removes friction. Customers perceive what we do differently.

TH: Even Cloudera will say their "whole backs" are open source. We are working under the meritocracy of the ASP with everything we ship and we are committed to 
continuing to do that. Cloudera may say they are open source, but they are closed-community for a subset of their projects. They also charge specific license
fees and up-charges for these investments. We don't operate that way. We are a support subscription company. We are kind of like an insurance company for Hadoop.

## RZ: So you would say Cloudera effectively doesn't run "pure Hadoop"?

AM: It's not necessarily purity in terms of code, it's more purity in terms of intent. It's an approach to how softare is developed.

TH: Our approach is that open source will maximize the value for our customers, always. There's no question as to whether the customer will get the best
of the community. Here are some statistics. At Oracle, software releases would take somewhere between 6-12mo to get through QA. Now, we close out in 2 months.
We are running thousands of test cases every night, and extra testing is done by the community members. As you exercise more code paths, code quality goes up.
This has been able to unleash innovations for our customers.

## BA: One last question: In having a front-row seat on these changes, what do you think the role of data will be in the next 5 years.

AM: Instead of 5 years out, let's talk a bit about what is happening now. There are many more communication options. Last week, I was in Texas talking to an
oil and gas company. Every car being manufactured today has a SIM card. 92% of the world today that an O&G company cares about has connectivity. 84% of that has
4G. There are more channels to send data on, there is cheaper infrastructure to store it on, and there will be much more custom hardware. I don't know if you 
track this, but I'm a geek. Intel has opened up a lot of their fabs for the very first time in the last 12 months. You can go to Intel and get them to manufacture
a fab you want. There is a lot of innovation that will be released this way as well. It makes it impossible to guess what it will lead to - but you know that
a lot will happen.

TH: Think about the power of computing with Raspberry Pi and that analytics can be done locally. The whole IoT revolution is going to drive more storage and a need
for analysis. And at the other end, there will be more of a need and an ability for predictive analytics and alerting. I have massive amount of my exercise
regimen over the past five years. Can I send that to my doctor and get more nuanced advice? It's a very interesting time. Managing a dynamic interface and 
engagement is a powerful experience, that is supported by data.

<figure>
	<a href="https://vimeo.com/119559165" target="_blank"><img src="/images/Arun_Tim_Play.png"></a>
	<figcaption>Please click here to watch an original link of the video.</figcaption>
</figure>

## Additional Q&A

* In open source, how to do you manage the scope and modularity of a project to prevent a "too many cooks in the kitchen" issue?
* What has Yahoo earned from opening up the IP for Hadoop? It seems like much of the value has gone to Hortonworks or Cloudera?
* In terms of testing, how do you ensure that all the use cases are covered when testing is distributed?
* Knowing we have a bunch of folks thinking about their careers, what advice you would give for being able to stay at the "edge"
of development?



[1]: https://sdsi.stanford.edu/
[2]: http://web.stanford.edu/group/informs/cgi-bin/
[3]: http://www.wired.com/2013/07/hadoop-yarn/
[4]: https://twitter.com/TimHallHWX?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor
[5]: http://stanford.edu/~rezab/
[6]: https://databricks.com/
[7]: https://en.wikipedia.org/wiki/Rasmus_Lerdorf
[8]: http://www.infoworld.com/article/2876240/hadoop/hortonworks-plans-for-hadoop-data-governance.html