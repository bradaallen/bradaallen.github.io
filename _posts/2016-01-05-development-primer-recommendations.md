---
layout: post
title: "Development foundations for being data-driven."
modified:
excerpt: "A few book recommendations for understanding new developments in software."
comments: true
tags: []
---

*UPDATE: My colleague Fausto recently had a great article around the relationship between [data systems and DevOps][1] - my favorite quote was, “If you are on the path to being a data-driven company, you have to be on the path to being a development-enabled company.”*

##Getting Started

Understanding the relationship between software development and data science is important: it helps ensure that solutions are scalable, responsive, and accurate; it also helps ensure that one is hiring and nurturing complementary talent for putting algorithms and data products into production. Thinking about this, I put together a list of books that have helped me get a sense of modern innovations: from database types to continuous delivery practices to test-driven or behavior-driven development. We benefit from these innovations every day: 

* Evolutions in distributed computing form the basis of cloud services (thanks Gmail!)
* Key-Value Store databases are great for storing shopping cart information (thanks Amazon!)
* Continuous Delivery is one thing that allows Facebook to [“Move Fast and Break Things.”][2]

So, getting a sense of how these things work is a good start for being able to understand where the trends are going and how they might be useful for a business undergoing a digital transformation. For each book, I include a small description and, at the end, give some suggestions for staying fresh with architectural development.

* **[NoSQL Distilled][3]:** [Martin Fowler and Pramod Sadalage][3]
* **[Continuous Delivery][4]:** [Jez Humble and David Farley][4]
* **[Specification by Example][5]:** [Gojko Adzic][5]

##NoSQL Distilled

This book is a great read for being introduced to the many different types of databases that have emerged as the use of distributed computing has grown. The book also walks through concepts present in distributed computing (e.g., ACID vs. BASE, the [CAP Theorem][6] , types of sharding, and read-write availability).

NoSQL is a broad-based term that refers to schemaless databases. Some schema/structure is required to make sense of the data, but this can be provided de facto by the application language (implicit schema). Traditional RDBMS have a lot of utility; NoSQL databases (e.g., Key-Value, Document, Column-Family, Graph) have led to a rise of polyglot persistence - which refers to combining different database models when appropriate to serve an application’s needs. *UPDATE: A few examples of when (and when not) to use different databases can be found [at this link.][7]*

The book describes two key reasons to use NoSQL technology as being:

* To improve programmer productivity by using a database that better matches an application’s needs
* To improve data access performance via some combination of handling larger data volumes, reducing latency, and improving throughput

Service encapsulation supports changing data storage technologies as needs and technology evolve. This book may be a good start to considering [microservices architectures][8]; turning parts of applications into services also allows an architect to introduce NoSQL into an existing application. Considering the bullet points above, it’s also important to note that testing expectations about programmer productivity and/or performance should be done before committing to using these technologies.

##Continuous Delivery

Continuous Delivery refers to a software development discipline in which software is built in such a way that it can be deployed at any time. This book popularized the term “bring the pain forward” - which refers to the practice of trying to create a testing environment in which small changes are pushed to production, the developer knows if the push was successful almost immediately, and that developer becomes responsible for fixing the code if there is a break. Microsoft recently [shared their engineering journey to Continuous Delivery][9], noting that “Engineers begin to riot if we deploy less than 10x per week.”

The book is divided into three sections:

* *Foundations:* This section outlines principles any organization should follow in setting up a Continuous Delivery infrastructure.
* *Deployment Pipeline:* This walks through different stages of the pipeline, with a focus on scripting, the commit stage, and testing.
* *Delivery Ecosystem:* This details the ongoing management of delivery, including compliance, version control, components, dependencies, data, etc.

<figure>
	<img src="/images/deploymentpipeline.png">
	<figcaption>Getting from commit to release.</figcaption>
</figure>

One key principle of continuous delivery is automation. This should be the only way in which the software is ever deployed. The remedy is to integrate the testing, deployment, and release activities into the development process. Make them a normal and ongoing part of development so that by the time you are ready to release your system into production there is little to no risk, because you have rehearsed it on many different occasions in a progressively more production-like sequence of test environments.

Another is frequent release of software to production. If releases are frequent, the delta between releases will be small. This significantly reduces the risk associated with releasing and makes it much easier to roll back. Frequent releases also lead to faster feedback—indeed, they require it. Much of the book concentrates on getting feedback on changes to your application and its associated configuration (including its environment, deployment process, and data) as quickly as possible. Anything that changes between environments should be captured as configuration information. 

Finally, a third principle is continuous collaboration. It is essential that everybody involved in the process of delivering software is involved in the feedback process. That includes developers, testers, operations staff, database administrators, infrastructure specialists, and managers. When something needs doing, it is the responsibility of the whole team to stop what they are doing and decide on a course of action. Only once this is done should the team carry on with their work.

##Specification by Example

Specification by Example is a reference to a practice very similar to Test-Driven Development (TDD) or Behavior-Driven Development (BDD). It walks through a process for articulating clear software product specifications that are easily understood by both the business side and engineers. These principles are important because: (1) they allow for precise testing, and (2) as such, they shorten the time between idea-generation and deployment. This, with process automation, is a key component of Continuous Delivery. 

<figure>
	<img src="/images/livingdocumentation.png">
	<figcaption>What living documentation is all about.</figcaption>
</figure>

The book reminds me of one of my favorite books on product management: Bob Cooper’s [Winning at New Products][10]. Both have a focus on managing the risk inherent in cross-functional / interdisciplinary teams and ask, *“How can I develop the right common language to foster communication and improve decision making?”* Specification by Example can be long at times, especially if you already accept the benefits of design thinking. It spends a lot of time focusing on how companies can make the transition to adopting Specification by Example practices and highlighting case studies of how it has been done by others. For me, I got a huge value from learning about living documentation.

Living documentation is a process by which the tests in the deployment pipeline are synonymous with the product specifications - the product specifications are executable. An automated Specification with Examples that is comprehensible and accessible to all team members becomes an executable specification. This can be used as a target for development and easily check if the system does what was agreed on, and the same documentation provides clarification for business users. If a specification needs changed, it changes is only one place.

When a software system is continuously validated against a set of executable specifications, a team can be certain that the system will do what the specifications say—or, to put it differently, that the specifications will continue to describe what the system does. Those specifications live with the system, and they’re always consistent.

Living documentation also fosters collaboration. It allows teams to join together and analyze the impact of proposed changes and discuss potential solutions. It also allows them to make use of existing documentation by extending it for new requirements. Instead of relying on a single person to get the specifications right in isolation, successful delivery teams collaborate with the business users to specify the solution. Pretty cool!

##How to stay up to date?

Again, these are books that have been pointed in my direction to understand some of the recent innovations in building robust, scalable systems. The best way to know what is useful, though, is to study what is being done in practice. Fortunately, the engineering teams of many large technology companies write about these frequently on their own blogs, for example:

* [Data Infrastructure at AirBnb][11]
* [Uber's Schemaless Datastore with MySQL][12]
* [Netflix - A Microscope on Microservices][13]
* [A Beginner's Guide to Scaling to 11M users on AWS][14]

To stay up to date on what these companies are trying (and “why”), you can add these sites to an RSS feed. They are also frequently shared on [Hacker News][15]. 
 


[1]: http://www.svds.com/connecting-data-systems-and-devops/
[2]: https://xkcd.com/1428/
[3]: http://www.amazon.com/NoSQL-Distilled-Emerging-Polyglot-Persistence/dp/0321826620
[4]: http://www.amazon.com/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912
[5]: http://www.amazon.com/Specification-Example-Successful-Deliver-Software/dp/1617290084
[6]: http://www.julianbrowne.com/article/viewer/brewers-cap-theorem
[7]: http://bradaallen.com/database-primers/
[8]: http://martinfowler.com/articles/microservices.html
[9]: http://stories.visualstudio.com/bing-continuous-delivery/
[10]: http://www.amazon.com/Winning-New-Products-Creating-Innovation/dp/0465025781
[11]: http://medium.stfi.re/airbnb-engineering/data-infrastructure-at-airbnb-8adfb34f169c?sf=dyyrrp#.y25n7dfss
[12]: https://eng.uber.com/schemaless-part-one/
[13]: http://techblog.netflix.com/2015/02/a-microscope-on-microservices.html
[14]: http://highscalability.com/blog/2016/1/11/a-beginners-guide-to-scaling-to-11-million-users-on-amazons.html
[15]: https://news.ycombinator.com/