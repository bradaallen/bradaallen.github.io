---
layout: post
title: "Database Primer: HBase"
modified:
excerpt: "Figuring out what HBase is all about."
comments: true
tags: []
---

A key tension when choosing an infrastructure concerns how to manage product performance with issues of extensibility (ie, confidence in future usability of a language or tool) and ongoing maintenance. Part of this tension is that infrastructure management is a dynamic effort. For example, distributed (and/or NoSQL) systems, but they [only become pertinent as a company’s user base moves into the millions (or tens of millions)][1]. This is the point at which the organization might run into database issues around contention with the write master, which basically means you're sending too much write traffic to one server.

Part of the tension is rooted in experience: large companies, some of whom may have little experience with managing a digital-scale infrastructure, are being asked to adopt these evolving technologies that require a very specific skillset. On top of this, a common adage is that [the best operators won't use a component until they know how it breaks][2]. So, how might one generate this experience?

To start, I’ve pulled together a few primers on more commonly used NoSQL databases to give a sense of:

* When they are used (use cases), and
* Common considerations / limitations / challenges

We’ve covered MongoDB [in a prior post][3]—for this one, let’s look at HBase. 

##HBase Background

[HBase][4] is an open source, non-relational, distributed database modeled after Google's BigTable and is written in Java. It is developed as part of Apache Software Foundation's Apache Hadoop project and runs on top of HDFS (Hadoop Distributed File System), providing BigTable-like capabilities for Hadoop.

HBase’s use has grown since being tapped to support [Facebook’s Messenger application in 2010][7]. Some characteristics of HBase:

* Has a simpler consistency model than Cassandra.
* Very good scalability and performance for their data patterns.
* Most feature rich for their requirements: auto load balancing and failover, compression support, multiple shards per server, etc.
* HDFS, the filesystem used by HBase, supports replication, end-to-end checksums, and automatic rebalancing.

HBase depends on all nodes in the cluster having closely synchronized clocks and referring to each other consistently. Using NTP and DNS ensures that you won’t run into odd behaviors when one node A thinks that the time is tomorrow and node B thinks it’s yesterday.

##When should you look at HBase?

* Your application has a variable schema where each row is slightly different
* You can’t add columns fast enough and most of them are NULL in each row
* You find that your data is stored in collections, for example some metadata, message data or binary data that is all keyed on the same value
* You need key based access to data when storing or retrieving

Common Considerations with HBase:

* *HBase doesn’t talk SQL, have an optimizer, or support cross record transactions or joins.*
* *Be careful when running mixed workloads on an HBase cluster.* When you have SLAs on HBase access independent of any MapReduce jobs (for example, a transformation in Pig and serving data from HBase) run them on separate clusters. 
* HBase is CPU and Memory intensive with sporadic large sequential I/O access while MapReduce jobs are primarily I/O bound with fixed memory and sporadic CPU.* Combined these can lead to unpredictable latencies for HBase and CPU contention between the two. A shared cluster also requires fewer task slots per node to accommodate for HBase CPU requirements (generally half the slots on each node that you would allocate without HBase). 
* *Keep an eye on memory swap.* If HBase starts to swap there is a good chance it will miss a heartbeat and get dropped from the cluster. On a busy cluster this may overload another region, causing it to swap and a cascade of failures.
* *Compactions that disrupt operations.* HBase like most other NoSQL databases, stores disk writes in a sequential fashion in a write-ahead log. However, these logs at some point have to be merged and reconciled leading to heavy disk I/O. These I/O storms called compactions, significantly slow down the application and lead to spikes in response time, affecting system reliability and performance.
* *Very slow crash recovery.* When a node fails in an HBase cluster, it could easily take between 30 minutes and 4 hours to recover it. This is because HBase relies on a RegionServer architecture that has several moving parts that need to be reestablished and realigned for the database to come back to normal operations.
* *Unreliable splitting.* When one region has too much data, it needs to be split into two, leading to system unreliability. Users have tried to avoid the issue by pre-splitting the tables that requires a lot of manual work and guesstimating the size of the regions.

Hopefully this record helps clarify some situations in which HBase might be useful, and some associated maintenance considerations. Many thanks to these articles as the primary references when putting this together:

* [HBase Operations and Best Practices (LinkedIn Blog)][5]
* [Apache HBase Do’s and Don’ts (Cloudera)][6]
* [Facebook's New Real-Time Messaging System: HBase To Store 135+ Billion Messages A Month (High Scalability)][7]
* [Avoiding HBase Reliability Problems (Toad World)][8]



[1]: http://highscalability.com/blog/2016/1/11/a-beginners-guide-to-scaling-to-11-million-users-on-amazons.html
[2]: http://firstround.com/review/the-three-infrastructure-mistakes-your-company-must-not-make/
[3]: http://bradaallen.com/database-primer-mongodb/
[4]: https://hbase.apache.org/
[5]: http://www.slideshare.net/vanuganti/hbase-hadoop-hbaseoperationspractices
[6]: https://blog.cloudera.com/blog/2011/04/hbase-dos-and-donts/
[7]: http://highscalability.com/blog/2010/11/16/facebooks-new-real-time-messaging-system-hbase-to-store-135.html
[8]: http://www.toadworld.com/platforms/nosql/b/weblog/archive/2013/10/14/avoiding-hbase-reliability-problems