---
layout: post
title: "Database Primer: MongoDB"
modified:
excerpt: "Figuring out what MongoDB's all about."
comments: true
tags: []
---


A key tension when choosing an infrastructure concerns how to manage product performance with issues of extensibility (ie, confidence in future usability of a language or tool) and ongoing maintenance. Part of this tension is that infrastructure management is a dynamic effort. For example, distributed (and/or NoSQL) systems, but they only become pertinent as a company’s user base [moves into the millions (or tens of millions)][1]. This is the point at which the organization might run into database issues around contention with the write master, which basically means you're sending too much write traffic to one server.

Part of the tension is rooted in experience: large companies, some of whom may have little experience with managing a digital-scale infrastructure, are being asked to adopt these evolving technologies that require a very specific skillset. On top of this, a common adage is that [the best operators won't use a component until they know how it breaks][2]. So, how might one generate this experience? 

To start, I’ve pulled together a few primers on more commonly used NoSQL databases to give a sense of:

* When they are used (use cases), and
* Common considerations / limitations / challenges

Let’s begin with [MongoDB][3], a popular document-oriented database. It is used by organizations of all sizes to power mission-critical, operational applications where low latency, high throughput and continuous availability are critical requirements of the system—you think about using MongoDB when you need fast use cases that can’t fail. 

##MongoDB: A Background

MongoDB provides horizontal scale-out for databases using a technique called sharding, which is transparent to applications. MongoDB distributes data across multiple Replica Sets called shards. Sharding is basically when datasets are split amongst multiple servers (e.g., by name: A-G in Server 1, H-R in Server 2, and S-Z in Server 3, or by geography: I am in the West Coast Server and my parents are in the East Coast Server).

With automatic balancing, MongoDB ensures data is equally distributed across shards as data volumes grow or the size of the cluster increases or decreases. Sharding allows MongoDB deployments to scale beyond the limitations of a single server, such as bottlenecks in RAM or disk I/O, without adding complexity to the application. MongoDB supports three types of sharding policy, enabling administrators to accommodate diverse query patterns: 

* *Range-based sharding:* Documents are partitioned across shards according to the shard key value. 
* *Hash-based sharding:* Documents are uniformly distributed according to an MD5 hash of the shard key value.
* *Location-aware sharding:* The data set needs to be assigned to a specific data center to support low latency local reads and writes. 

##Common Considerations with MongoDB

* *The obstacles to scaling performance as your usage grows may not be what you'd expect.* Performance bottlenecks usually are (in this order):
	* Sub-optimal schema design for application access patterns
	* Poor or missing indexes, occasionally too many unneeded indexes
	* Slow disks/insufficient disk IOPS for workload, especially to the write throughput
	* Insufficient RAM for indexes, will cause a lot of page faulting
* *Replica set health is more than replication lag.* "Replication lag," which is a measure of how far a secondary is behind the primary, is just one indicator of the health of your replica sets. Just as important as monitoring replication lag is keeping an eye on your replication oplog window. 
* *Place your database server at the inner data storage layer.* If public network exposure is combined with lack of access control, the entire content of the database is up for grabs for anyone who cares to look. In addition, an attacker could intentionally or accidentally change the database configuration, modify the application behavior or perform a Denial of Service (DoS) attack. It is surprisingly common to deploy MongoDB database servers directly online or in a DMZ.
* *MongoDB’s map-reduce functionality just isn’t meant for real time computing.* It is extremely slow, especially when you have a large amount of data in a sharded environment. Especially in a sharded mongoDB setup the I/O load increases rapidly with growing data, so fast disks are even more important than computing power or even memory for scaling your mongoDB servers.
* *The debugging experience is very painful.* There is no proper debugger, no console.log. The best tool you have is conditionally throwing, because the only thing you can get back from a MapReduce operation is the final data or the first uncaught error (which stops the operation). That’s annoying when your map or reduce or finalize function gets above 30 lines. 
* *The user will need to start with an intuition of chunks and sharding protocol.* MongoDBs documents are stored in so called chunks. For each chunk the maximum and minimum shardKey as well as the location (on which shard it is stored) and its size are known. Now when another document is inserted it will be stored within the chunk with the fitting id (shardKey) range. Then a few things happen:
	* If you are lucky and the shards are balanced already, and the document doesn’t increase the chunks size over a given limit, thats just it, the document is inserted and you are fine. 
	* If the document exceeds the chunks size limit, the chunk will be split into two different chunks. 
	* And if the shards are unbalanced, on top of that the new chunk will be moved to another shard. The split is a rather inexpensive operation, but moving the data to a different shard can be very expensive.

Hopefully this record helps clarify some situations in which MongoDB might be useful, and some associated maintenance considerations. Many thanks to these articles as the primary references when putting this together:

* [10 Things You Should Know About Running MongoDB at Scale (High Scalability)][4]
* [MongoDB Security Part II: 10 mistakes that can compromise your database (MongoDB blog)][5]
* [MongoDB – the pitfalls and how to avoid them (Mayflower)][6]
* [Read before considering using MongoDB for your next app (Long Term Laziness)][7]


[1]: http://highscalability.com/blog/2016/1/11/a-beginners-guide-to-scaling-to-11-million-users-on-amazons.html
[2]: http://firstround.com/review/the-three-infrastructure-mistakes-your-company-must-not-make/
[3]: https://www.mongodb.com/
[4]: http://highscalability.com/blog/2014/3/5/10-things-you-should-know-about-running-mongodb-at-scale.html
[5]: http://blog.mongodb.org/post/87691901392/mongodb-security-part-ii-10-mistakes-that-can
[6]: https://blog.mayflower.de/2408-MongoDB-the-pitfalls-and-how-to-avoid-them.html
[7]: https://longtermlaziness.wordpress.com/2012/08/24/a-post-you-wish-to-read-before-considering-using-mongodb-for-your-next-app/
