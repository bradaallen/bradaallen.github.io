---
layout: post
title: "Database Primer: Redis"
modified:
excerpt: "Figuring out what Redis is all about."
comments: true
tags: []
---


A key tension when choosing an infrastructure concerns how to manage product performance with issues of extensibility (ie, confidence in future usability of a language or tool) and ongoing maintenance. Part of this tension is that infrastructure management is a dynamic effort. For example, distributed (and/or NoSQL) systems, but they [only become pertinent as a company’s user base moves into the millions (or tens of millions)][1]. This is the point at which the organization might run into database issues around contention with the write master, which basically means you're sending too much write traffic to one server.

Part of the tension is rooted in experience: large companies, some of whom may have little experience with managing a digital-scale infrastructure, are being asked to adopt these evolving technologies that require a very specific skillset. On top of this, a common adage is that [the best operators won't use a component until they know how it breaks][2]. So, how might one generate this experience?

To start, I’ve pulled together a few primers on more commonly used NoSQL databases to give a sense of:

* When they are used (use cases), and
* Common considerations / limitations / challenges

We’ve covered [MongoDB][3] and [HBase][4] in prior posts—for this one, let’s look at Redis. 

##Redis Background

[Redis][5] is an in-memory data structure store frequently used as a database, cache, or message broker. It is popular with developers because of its versatile, optimized data structures -- sets, sorted sets, hashes, lists, strings, bit arrays -- which deliver efficient in-database operations such as set comparisons, list pull-push operations, and range queries.

Redis is also used for sessionizing data. Every event collected from an application or website belongs to a session that a user starts against Redis. Documents with tens or thousands of events create a stream of data that requires some amount of unraveling. When there are hundreds and thousands of users, event streams related to many users are interleaved. Updating each document with many small updates can be accomplished with disk-based MongoDB, but the expense of the operation is high and Redis’ hash data structure can make short work of the problem.

Hashes can be used to store event data by session. Keeping track of sessions that need to be timed out is also nontrivial when there are thousands of sessions, but Redis has built-in key expiration and timeout setting functionality that can be used to end sessions. Keyspace notifications allow users to subscribe to expired events and trigger an offload to MongoDB.

##Common Considerations with Redis

* *Redis doesn't provide sharding.* You should probably assume that you'll grow beyond the capacity of a single Redis server (slaves are for redundancy, not for scaling, though you can offload some read-only operations to slaves if you have some way to manage the data consistency --- for example the ZSET of key/timestamp values describe for expiry can also be used for some offline bulk processing operations; also the pub/sub features can be used for the master to provide hints regarding the quiescence of selected keys/data.
* *Consider writing your own abstraction layer to provide sharding.* Basically imagine that you have implemented a consistent hashing method ... you run every synthesized key through that before you use it.  
* *Choose consistent ways to name and prefix your keys.* Manage your namespace. Create a "registry" of key prefixes which maps each to your internal (perhaps wiki) documents for those application which "own" them.
* *Design, implement and test the mechanisms for garbage collection and/or data migration* for every class of data you put into your Redis infrastructure.
* *Design, implement and test a sharding (consistent hashing) library before you've invested much* into your application deployment and ensure that you keep a registry of "shards" replicated on each server.
* *Isolate all your K/V store and related operations into a your own library/API or service* And absolutely enforce the use of that API/service with an unrelenting and mercilessly iron hand.
* *Don't run out of RAM.* You need enough RAM to hold your entire set of data. Don't expect to be able to query data like in a database.  The paradigm of searching data is completely different. 

Hopefully this record helps clarify some situations in which Redis might be useful, and some associated maintenance considerations. Many thanks to these articles as the primary references when putting this together:

* [What are 5 mistakes to avoid when using Redis? (Quora)][6]
* [MongoDB and Redis pair volume with velocity (InfoWorld)][7]


[1]: http://highscalability.com/blog/2016/1/11/a-beginners-guide-to-scaling-to-11-million-users-on-amazons.html
[2]: http://firstround.com/review/the-three-infrastructure-mistakes-your-company-must-not-make/
[3]: http://bradaallen.com/database-primer-mongodb/
[4]: http://bradaallen.com/database-primer-hbase/
[5]: http://redis.io/
[6]: https://www.quora.com/What-are-5-mistakes-to-avoid-when-using-Redis
[7]: http://www.infoworld.com/article/3008052/nosql/mongodb-and-redis-pair-volume-with-velocity.html