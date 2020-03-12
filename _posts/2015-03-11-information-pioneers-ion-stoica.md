---
layout: post
title: "Information Pioneers: A Conversation with Ion Stoica."
modified:
excerpt: "The CEO of Databricks discusses evolutions in distributed computing."
comments: true
tags: [Databricks, Spark, distributed computing, Information Pioneers, Britt Jamison, Stanford, Berkeley, information, data science, data, CS, technology]
---

*Information Pioneers is a series I helped start in 2014 as part of [SDSI][1], the Stanford Data Science 
Initiative. The goal was to bring thought leaders to campus to help students learn from visionaries in
the data science field. It is currently hosted by the [INFORMS chapter][2] at Stanford.*

*[Ion Stoica][3] is the CEO of [Databricks][4], and, at Berkeley, is a professor in CS and the former 
Director of the [AMP Lab][5]. Ion was interviewed by my colleague Britt Jamison. Errors and omissions are my own, 
and any good stuff can be completely credited to them.*

<figure>
	<img src="/images/Ion_Britt.png">
	<figcaption>Ion and Britt for Information Pioneers.</figcaption>
</figure>

## Off the bat, let's talk a bit about Databricks. Some folks might be familiar with Spark, but not Databricks - tell us more about that.

Databricks was founded in 2013. It is based around commercializing Spark, a project started in 2009 in Berkeley
and open sourced in 2010. In terms of the product, Databricks is providing a hosted service which is based on
Spark and the vision of the company is to simplify big data. Our aim is to build a platform in which you can run
your data pipeline from data ingestion, preparation, interactive query processing, insights from
machine learning, graphics, algorithms, all the way to data products. 

## You have been working around data for a long time. What initially got you interested in the field?

We started at Berkeley with these "Five Years Labs." They try to serve big problems. Right now, we are doing
AMP Lab - the previous lab was called RAM Lab, and was built around cluster computing. That was started around
2006. That got us in touch with a few companies, including Facebook. Their big data cluster was 80 nodes, and their
team was 3 people - they hired a few folks from Yahoo and started doing new stuff, which was Hive on top of Hadoop. 
We started to work with them and then [Matei Zaharia][6] ended up creating Spark. 

The first problem we tried to address with Facebook was getting around this problem of batch process and 
scheduling. Basically, Hadoop initially was a batch-processing system, with many jobs are submitted in a queue,
and you process them in the order in which they arrive. This means, when you have a huge job of a few
hours, the subsequent jobs, even if small, have to wait after a big job. We developed then an algorithm called "file
sharing" which has become a popular scaling algorithm for Hadoop. It basically tries to create different queues and 
partitioned resources across jobs to process orders in tandem, large and small.

The other thing we worked on in 2006 was founding this company, [Conviva][7]. Conviva was peer-to-peer distribution. The 
application was video distribution. Quite soon, we switched from P2P to a model that uses existing distribution infrastructure,
but we aggregated the intelligence and the decision-making. Still today, our customers are premium content providers. For example,
we power HBO GO and MLB and places like this. We provide a service of real-time analytics: we take information from all of our
clients and we aggregate them. We answer questions like, "Are there buffers? What is the bitrate we are streaming at?" The 
other side tries to provide hints to the clients about optimal bitrates and streaming for clients. That was the vision: 
real-time analytics and real-time control. Even then, it was big data. Right now, we have approximately 1 million clients at 
any given time. Then, Hadoop was only for historical data and batch computation. We started to build home-grown solutions, 
for streaming and for real-time control. We needed a distributed infrastructure for that. When I came back to Berkeley, 
I knew there were big problems - I had seen that. 

The third thing was, in the [RAD Lab][8], we were working next to the machine learning folks. And they wanted to do it at 
scale. Implementation at that time was very slow. Hadoop and MapReduce at that time were not very mature. Each ML algorithm
is about iteration and converging to a great model. Each iteration on Hadoop is a MapReduce job. Between each job, the data
gets written to disc on HDFS, and the next iteration needs to read it. This is very slow! We have this use case scenario: real-time
streaming, real-time decisions, interactive query processing, iterative algorithms. When I got back to Berkeley, I had this
seminar in 2009. These are one of the perks of the jobs. We had about 30 students discussing the problems in cloud computing
and we would have class projects. One of the projects was [Mesos][9]. That was one of the first systems we started to build.

Mesos was a system that allowed multiple cluster computing frameworks to run on the same cluster. We were expanding the idea
from the Facebook case (jobs of different size). There are really different categories of jobs and they can run on different
cluster computing frameworks. For instance, MapReduce, or streaming systems like [Storm][10], or [MPI][11] in 
high-performance computing. At that point, you have to create a cluster for everyone, but you don't want that 
because it is very expensive. And how are you going to share data between the clusters? That is basically Mesos - trying 
to solve this problem for data centers. Writing multiple applications on one machine. Now, how do you illustrate and evaluate 
Mesos? You run MapReduce, and MPI, and many variations of MapReduce at the same time. This is pretty cool, but Mesos is 
something like an operating system. It provides a lot of services, provides a lot of plumbing. If a node fails, it thinks 
it is down, it tries to provide isolation between different slices of computing frameworks. We said, well - another way to 
evaluate this is to show it is much easier to develop a new class of computing framework on top of it because we an leverage 
all of the services of Mesos. There is no need for the services to do themselves, like scheduling. The first framework 
we developed was Spark. We said, ok, Hadoop-MapReduce is good at batch processing, so we are going to target some of 
the workloads we knew from our experiences in industry that are important. We focused on interactive query processing and 
iterative algorithms. [Spark][12] was created towards the end of 2009.

## What a great history. It seems like a lot of tools have been developed since the 2002-2004 timeframe. What was the impetus for these tools to be developed? You have been fortunate to be in Silicon Valley - is this coming from a business need, or from the technical side? That is, there is so much data and processing to do that new tools need to be developed.

That is definitely the case, the latter. Many great ideas come from solving real problems. [MapReduce comes from Google in 2004][13]. 
It was a great piece of work. They had to process a huge amount of data, and needed a flexible system to do that. What were the
choices at that time? One one hand, they could buy a big database: very expensive and inflexible. On the other hand, they
could use some of the high performance computing software. That could be another. But that doesn't really match the problem.
They wanted to do ever growing amounts of data, cheaply. They had to solve the problem - they wanted to run the system, the software,
on commodity hardware. The more nodes one has, the higher the probability of failure. There are software failures, and there
are hardware failures. You need something fault tolerant. This is one of the places HPC fell short. They are supposed to run
on supercomputers, which are very expensive. If there is a crash, they have to rerun the program. So, MapReduce - run on commodity
software and be fault tolerant. The way it was fault tolerant: there are two stages, Map and Reduce, and each stage consists
of a set of task and if one stage fails, the schedule has enough information about what has failed and it recovers that task
by rerunning that task on the input data. The input data is typically replicated on three different nodes, so one can survive on
two node failures or one direct failure. Very nice solution, general, flexible, and simple.

## We talk a lot about MapReduce, which is maybe one of the most important papers written in the last 20 years. Now, some people are saying MapReduce is dead. Do you think so?

So, MapReduce is a logical decomposition of a parallel program. As a second item, MapReduce is an artifact, an implementation.
I think it was a great first system. But in any area where there is a lot of work, there is a lot of progress. We learned a lot
from MapReduce, and now there are second generation systems that are better. We generalize MapReduce and extend it, to get
higher performance. One of these systems is Spark. It's not about MapReduce about being dead, it is about a new generation that
generalize and expands the framework.

## So, do you see Spark as solving some of the problems with the MapReduce portion of Hadoop? Or do you see Spark as part of a larger system?

That's a very good question. Right now, there are three main layers to Hadoop. First, the Hadoop Distributed File System, which
is HDFS. Then there is [YARN][14], which is similar to mesos mentioned earlier and supports different frameworks. And then on top 
of that, one framework is Hadoop MapReduce. Spark is an execution engine, a cluster computing framework, that is roughly at the
same level as Hadoop MapReduce. On one side, Spark runs in the Hadoop ecosystem. If you have data in HDFS you can run Spark and
process the data in HDFS. On the other side, because it is a general cluster computing framework, Spark doesn't necessarily need
HDFS and it can consume data from other distributed storage systems. "Running in the cloud" is on S3. Or from [Cassandra][15]. 
[GlusterFS][16]. One one hand it can be a part of a Hadoop stack, which occurs in many cases. There are also other contexts or
deployments in which it is used.

## I want to get into some of the problems Spark is solving. There is also a pretty big theme here of open source. It's just exploded in the last 5 or 8 years. Being very involved in this community, what are your thoughts on why it has exploded? And what do you think the impact will be going forward?

Again, a very good question. The interesting thing here is that open source is exploding in multiple areas. For big data,
it is one of the rare cases in which open source was the incumbent almost from Day 1. Google is very advanced, but everything
is closed and they do not commercialize the systems because they consider it a key asset and competitive advantage. Microsoft
has not moved that fast, despite being interesting, and has also not commercialized that work. We now have all of these 
startups beginning to get a lot of data - in particular Facebook and Twitter. And Yahoo creates Hadoop MapReduce. So everyone 
then takes Yahoo's open source, Oracle is expensive, and there are no commercial offerings. It has limitations, though, so 
people begin innovating on top of that, since it is with Apache. That was the core with where we started. Now, all of the big 
offerings are open sourced. 

There were quite a slew of companies in 2010-2012 that developed proprietary solutions to deal with Hadoop's limitations.
A new layer on top - cacheing for example. But there was so much energy going to open source, that it becomes difficult to
remain competitive in the long run and keep your advantage. Many of these companies over time then shift to open source, for
example, to Spark. 

## With regard to commercialization, I assume you are referring to companies like Cloudera, Hortonworks, MapR. Could you talk a bit about what that collaboration has been like?

Let me take a step back and talk a bit about our business, because I think it will help describe our relationship with
Hadoop distributors. When we started with Databricks, we asked ourselves, "What kind of company do we want to build?"
One obvious choice was to build something like Cloudera or Red Hat for Spark. We have our own distributions, and we support
that with professional services and things like that. We did not do that. We decided instead to go for a service offering
on the cloud. We saw it was the right time, and we saw it was in our DNA to go in that direction instead of a more support
heavy company. Our strategy then became very simple: first, we want Spark to be successful as open sourced. The more successful
Spark is, the more successful our services are. So, to promote this, we partner with the Hadoop distributors and encouraged
them to provide some level of support to make it comfortable to include Spark in their distribution.

## Could you explain a bit more about the cloud offering of Databricks? How do you see customers using your offering?

Fundamentally, "big data" work is pretty hard. What do you need to do this as a company? First, you have to put together
a Hadoop cluster, which is not easy. Maybe you can get Cloudera or Hortonworks to help you with that. Then, you need to
build a data pipeline on top of that. It is noisy, it needs to be cleaned, and turned into a table for interactive queries.
So, at this point, Hadoop is no longer enough. Maybe you need another open source system: [Presto][17] from Facebook, 
[Impala][18] from Cloudera, or [Drill][19] from MapR. This is just some exploration to get some idea about the data. 

Now you want more insights. To do that, you have to run some machine learning algorithms or graph algorithms. Maybe you 
want to productize these insights and develop a recommendation engine or something like that. One needs to deal and stitch 
together an extremely complicated system. This is where Databricks brings value. First, it uses Spark, which in itself 
is a unified engine. It supports batch processing, interactive query processing, streaming, machine learning, and graph 
processing. In addition, we also provide cluster management, which makes it very easy to spin off new clusters and scale 
them up and down, really in seconds. We then have a set of tools on top of that that make it much easier to interact 
with the data. We built a notebook for collaboration, there is interactive visualization, we can programmatically run 
jobs. The final piece is, "What are you going to do with the data?" Typically, you want reports or dashboards to share 
within the company. We make this very easy as well. 

This is what you get: tools and a cluster manager, that is packaged with Spark, and sold as a service. 

## You mentioned how difficult it is unlocking value from data. That is probably a bit of an understatement, right? 60% of data projects - maybe even higher - fail. What are your reasons for this challenge? And how does Databricks help this?

The tools are still at the beginning. We are very early on. It is command line debugging, as opposed to being in the IDE.
It's pretty different, right? It is the difference between interactive debugging and debugging with screen tests in a program.
The tools have a long way to go. The other reason for which there is no silver bullet... [there is an] assumption that, in the 
log, there is enough information to achieve the goal. This is sometimes not the case. You don't have the data, or the data
is too noisy. So the data itself is not enough to succeed. What can be done about this? Well, fail fast. Don't spend 6 months
and say, "Hey, there is not enough data." You want to say that in two weeks. So you can go back and say, "We need more logs."

So that's what it boils down to: not enough data, inaccessible or clunky tools, and not enough trained people. Training is
important. Data science today is a cool and hot job - but most people in industry don't have formal training. When Databricks
does training, we give out surveys. And 35% say they are data scientists and 40-50% say they are software engineers. When 
we ask them, where they are heading and where they want to go - now it is more like 50-55% of data scientists and 30% of 
software engineers. Many engineers want to be trained to become data scientists. 

## I like that you are speaking about skillsets in these organizations. We also are talking about Facebook and Google - do you think companies like Uber and Airbnb can also benefit from tools like Spark?

Well, they are definitely not small companies. And they can benefit - that is what is exciting about big data. It creates a
lot of value. It is a fascinating thing. At the end of the data, what is Google, Facebook, or Twitter? They are data companies.
That is where they are spending their engineering efforts. To build the tools, to build the systems, to mine the data, to
build the data products. You can also see how this data is disrupting traditional industries. At the end of the day, Uber is
building a pretty sophisticated infrastructure. Another example is Netflix. All of their infrastructure is in Amazon and it
is very sophisticated, and celebrated. So, a lot of these companies are more nimble in using the data. It is pretty easy to
get a lot of data. Successful applications will send a lot of logs back. The problem today is that many of these companies
hope to get some value from the data, but it is hard. We see a lot of use cases. This goes from small startups to large 
companies.

## Great, one last question from me. We've spent a lot of time describing the ecosystem today. What do you think the ecosystem is going to look like in five or ten years?

Yes, that's interesting. In order to get an answer, one should look at what has happened in other similar cases. There are
three phases. One phase is when a new problem creates a new technology to solve that problem. A second stage is the creation
of new use cases from the new technology and people building additional systems for each of them. The third is then a
consolidation. We have two examples for this. One, is mobile technology. Initially, it was the cell phone. There were new
capabilities, you can call from anywhere. Then, at the end of the 90s, there was a 2nd stage. People want to take notes/PDAs 
in addition to calls, or maps, or play games. You get a plethora of devices to cover these use cases. This consolidates into
a smartphone. And now there is a new wave: Waze, for crowdsourcing traffic, or Snapchat. They are possible because of this
integration that took place in disparate devices over 15 years.

Big data initially was MapReduce - a new problem with new technology. Right now, we are pretty much in the second stage.
You have a new workload? Build a new system. Machine Learning? Use [Mahout][20]. Graph processing? GraphLab or [Giraph][21]. 
Streaming? Storm. Interactive processing? Impala, or Drill. You want to put the system together, now, which is kind of hard. 
I think the next stage is going to be a consolidation. It may be Spark, or it may be something else. It will be a system or 
a platform that will allow you to run different workloads that create new applications. Let me give one example. Suppose you
have data streaming in, and you want to have interactive queries on the streaming data. Something happens, and you want to 
drill down in seconds. Today, in the traditional Hadoop ecosystem, it is very hard to do. How are you going to have Impala 
operating on the system in Storm? You cannot. You need the move the data through HDFS to Impala, which already defeats the 
goal of interactive querying streamed data. Something like Spark can do this. The workloads share the same engine and data 
structures. It is already in place. I think this is what will happen. 

<figure>
	<a href="https://vimeo.com/122465105" target="_blank"><img src="/images/Ion_Britt_Play.png"></a>
	<figcaption>Please click here to watch an original link of the video.</figcaption>
</figure>

## Additional Q&A

* How do you view innovation coming out of academia vs. the commercial world? For example, Tachyon and most recently Velox out of
AMP Lab.
* You discussed the importance of consolidating processing frameworks? What are your thoughts on using traditional storage,
like Oracle systems, and have the processing done where the data is ingested?
* In terms of testing, how do you ensure that all the use cases are covered when testing is distributed?
* Knowing we have a bunch of folks thinking about their careers, what advice you would give for being able to stay at the "edge"
of development?



[1]: https://sdsi.stanford.edu/
[2]: http://web.stanford.edu/group/informs/cgi-bin/
[3]: http://www.cs.berkeley.edu/~istoica/
[4]: https://databricks.com/
[5]: https://amplab.cs.berkeley.edu/
[6]: https://people.csail.mit.edu/matei/
[7]: http://www.conviva.com/
[8]: https://radlab.cs.berkeley.edu/
[9]: http://mesos.apache.org/
[10]: http://storm.apache.org/
[11]: http://www.open-mpi.org/
[12]: http://spark.apache.org/
[13]: http://research.google.com/archive/mapreduce.html
[14]: https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html
[15]: http://cassandra.apache.org/
[16]: http://www.gluster.org/
[17]: https://prestodb.io/
[18]: http://www.cloudera.com/content/www/en-us/products/apache-hadoop/impala.html
[19]: https://www.mapr.com/products/apache-drill
[20]: http://mahout.apache.org/
[21]: http://giraph.apache.org/


