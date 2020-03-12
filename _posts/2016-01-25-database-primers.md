---
layout: post
title: "Choosing a new database."
modified:
excerpt: "A few high-level considerations when updating an architecture."
comments: true
tags: []
---

I recently caught up with my colleague Gary (here’s an [article he wrote on microservices for SVDS][1]) to get his advice on choosing database systems: specifically, when to recommend certain databases, how to think about meeting a customer’s needs, incorporating user requirements into design, etc. He knows these things inside and out, having been heavily involved in open source development with Apache and a member of [Cassandra’s Project Management Committee][2].

Below, I include some of key use cases for modern database structures (and when not to use). In my conversation with Gary, I was most surprised by the human aspect of maintaining these systems - and how much of a priority it is to determine what’s feasible for a given organization based on their talent and expectations.

##Some key questions to explore when updating an architecture:
* **Maintenance & Hosted vs. On-Site.** Always be sure to ask, *“What are the ongoing maintenance requirements?”* 
	* For example, am I going to need to hire new staff? Do I have people that can already do this? 
	* If the answer is no (re: hiring) then maybe we need to swing to hosted systems. A lot of these big systems are rather high-maintenance. They require a lot of monitoring and operations people that know what is going on there. 
		* Note: The same is true for relational systems, except that relational systems are better understood and it is easier to find people who know those skills. Making sure that customers have a handle on maintenance req and ensuring they are comfortable with that. 
	* These are not things that will be fixed by QA. Discs getting full, servers going down, ongoing things like that. This is more about teaching, showing, and making sure that clients are prepared. 
* **Migrations.** What happens in 5, 10, 20 years when we want to migrate off of this system? I think about this - because I’ve been around when it happens. 
	* Migrations depend on how much data is in the system. If there are TB & TB of data, there are time and space constraints. The possibility of scheduling downtime for maintenance is less pragmatic. 
	* This is done through parallel updates and backfilling - systems run parallel with same data - then migrate applications over to new system, then shut the old system off. This is a pretty standard way of migrating off of a big data platform. Every once in awhile, folks will say, “Nope, I don’t mind having some downtime.” 
* **Developing Architectural Intuition.** Designing architectures well come from experience- from having bad deployments and seeing how things fail. A good start (if that experience is nascent) is to find blog posts in which people have complained about an installation. 
* **General Things to Cover:**
	* What is the actual size of the data corpus initially, and what does it grow to? Do I need one machine or a whole flock of machines? (Cassandra, Riak, Mongo)
	* For easy argument, what is going to be the ratio of reads to writes? Some systems have quicker writes, some have quicker reads. How difficult is it going to be to get data in and out of these systems? Some have good client libraries and some don’t. 
		* Cassandra has a good client ecosystem, but HBase doesn’t. 
		* Cassandra has SQL, HBase doesn’t. 

In the future, I hope to include more detail on situations in which certain database types might be preferred over other: for example, HBase's lack of SQL querying or Redis' lack of sharding. 

##First-pass: Key Use Cases for Schemaless Databases

####*Key-Value Store* (eg, BerkeleyDB, LevelDB, Memchached, Project Voldemort, Redis, Riak)

**Suitable Use Cases** | **When Not to Use**
Storing Session Information | Relationships among Data
User Profiles, Preferences | Structure of Data
Shopping Cart Data | Scaling
 | Multioperation Transactions
 | Query by Data
 | Operations by Sets

####*Document Databases* (eg, CouchDB, MongoDB, OrientDB, RavenDB, Terrastore)

**Suitable Use Cases** | **When Not to Use**
Event Logging | Complex Transactions Spanning Operations
Content Management Systems, Blogging | Queries against Varying Aggregate Structure
Web Analytics / Real-Time Analytics | 
E-Commerce Applications | 

Note: Documents are stored in the ‘Value’ part of a KV database.

####*Column-Family Stores* (eg, Amazon SimpleDB, Cassandra, HBase, Hypertable)

**Suitable Use Cases** | **When Not to Use**
Event Logging | Early Prototypes
Content Management Systems, Blogging | Initial Tech Spikes
Counters | 
Expiring Usage | 


Note: RDBMS impose high cost on schema change, which is traded off for a low cost of query change; in Cassandra, the cost may be higher for query change as compared to schema change.

####*Graph Databases* (eg, FlockDB, HyperGraphDB, Infinite Graph, Neo4J, Orient DB)

**Suitable Use Cases** | **When Not to Use**
Connected Data | 
Routing, Dispatch, and Location-Based Svcs | 
Recommendation Engines | 

Note: Graph databases provide the opportunity to store entities and relationships between entities. 



[1]: http://www.svds.com/evaluating-microservices-real-world-lessons/
[2]: https://wiki.apache.org/cassandra/Committers