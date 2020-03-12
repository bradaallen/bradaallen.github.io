---
layout: post
title: "Playing Around with Docker"
modified:
excerpt: "Taming the Whale."
comments: true
tags: []
---

<figure>
	<img src="/images/docker-jenkins.png">
	<figcaption>Refined delivery! (I love this image.)</figcaption>
</figure>

I recently completed a great Docker tutorial offered by [Prakhar Srivastav][1]. In this exercise, we set up [Docker][2], log into the DockerHub, and pull down “images.” We also publish these images to the web, and create a dynamic website using EC2 Container Service using AWS and two docker images networked together. 

## What is Docker? What are “containers”?

The industry standard today is to use Virtual Machines (VMs) to run software applications. VMs run applications inside a guest Operating System, which runs on virtual hardware powered by the server’s host OS.

VMs are great at providing full process isolation for applications: there are very few ways a problem in the host operating system can affect the software running in the guest operating system, and vice-versa. But this isolation comes at great cost — the computational overhead spent virtualizing hardware for a guest OS to use is substantial.

Containers take a different approach: by leveraging the low-level mechanics of the host operating system, containers provide most of the isolation of virtual machines at a fraction of the computing power. Docker specifically interacts directly with the Linux kernel. Containerization has grown rapidly, especially with the growth of cloud computing and services. For example, [Google launches roughly 2 billion containers per week][3]. 

Why has the containerization movement risen with cloud computing? This lower overhead means that [cloud providers like Amazon and others getting a 26 to 1 performance improvement on the virtual machines that they sell per hour][4]. It’s a huge enabler for their businesses because you’re suddenly able to do a lot more for the same price. Instead of needing to buy two virtual machines (for load balancing/availability) for every isolated application that you need to deploy, you could just cluster three larger VMs and deploy all of them to it, actual processor limits aside. It makes cloud computing cheaper for both AWS/Azure/GCP and the businesses consuming those services. When business makes cost-benefit decisions around cloud migrations, this resource efficiency creates a swing in favor of cloud providers.

On the other side of the equation, containerization is well-loved by developers because it de-risks creating production level software: 

* Your development team is able to create complex requirements for a microservice within an easy-to-write Dockerfile.
* Push the code up to your git repo.
* Let the continuous integration (CI) server pull it down and build the EXACT environment that will be used in production to run the test suite without needing to configure the CI server at all.
* Tear down the entire thing when it’s finished.
* Deploy it out to a staging environment for testers or just notify the testers so that they can run a single command to configure and start the environment locally.
* Confidently roll exactly what you had in development, testing, and staging into production without any concerns about machine configuration.

## What is an image?

You can think of a docker “image” as a fully packaged container. It includes all of the executable code for an application, as well as defines the packages and dependencies required to run the application effectively. Often, images can be automatically stood up on a server with a few lines of code. 

Images can also be shared publicly in the [Docker Store][5]. In the Docker store, you can find projects that other teams are willing to publish—helping you see pre-existing code or logic that may help you get your projects off the ground faster. In this sense, it has functionality similar to Github, a site in which teams manage version control of their codebase, but users can also publish and share their code publicly.

Prakar’s exercises involves loading a single image of cat photos, and then a slightly more complex site of two images networked together, seen here:

<figure>
	<img src="/images/foodtrucks.png">
	<figcaption>The final view of Prakhar's project.</figcaption>
</figure>

We also get experience with pushing containers to AWS’s EC2 Container Service. I would recommend closing down the instances once you get your IP address up and running / know the project is live — I found that hosting the project on 2 containers cost ~$50/month. 

In the above picture, the two images are a base image (the underlying map) and an elasticsearch image. This allows site owners to troubleshoot and edit different aspects of the site independently—for example, if aspects of the “search” experience were broken, users would still be able to utilize other parts of the site. This functionality also allows the site to scale only on the services that are finding increased use. 

## How does containerization enable microservices?

I was curious about Docker as a representation of the [microservices movement][6]. The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. In the last few years, it has become the default style for building enterprise applications and is considered to be a key enabler of software platforms. It is a validation of Jeff Bezos’s mandate to have all teams communicate their work through externalizable APIs (reference: [Steve Yegge’s insightful and fun “rant”][7]). 

<figure>
	<img src="/images/microservices.png">
	<figcaption>Differences between a "monolithic" and a "microservices" design.</figcaption>
</figure>

In service-oriented architectures (SOA), integration relies heavily on middleware, in particular enterprise service bus (ESB). Microservices architecture may often make use of a message bus, but there is no logic in the messaging layer whatsoever—it is purely used as a transport for messages from one service to another. This differs dramatically from ESB, which contains substantial logic for message routing, schema validation, message translation, and business rules. As a result, microservices architectures are substantially less cumbersome than traditional SOA, and don’t require the same level of governance and canonical data modeling to define the interface between services. (Source found [here][8].) 

Docker provides an isolation between containers running on the same host that makes deploying microservice code developed using different languages and frameworks very easy. Using Docker, we could create a DockerFile describing all the language, framework, and library dependencies for that service. With microservices, development is rapid and services evolve alongside the needs of the business. 

## What next?

*Understanding Benefits to Web Design, Challenges with Pipelines/Clusters:* In having conversation with data engineers at SVDS, we disucced the complications associated with Docker networking - which is a problem for distributed applications (Docker is trying to manage this with [Docker Swarm][9]). Their opinion was that it works great for web apps. It doesn’t really change “per environment.” These “scale out” in easily parallelizable ways. This gets a little bit tricker with things that have to communicate with each other—like Cassandra.

They questioned how well Docker could solve the problem of Spark executions. The class of applications in which things can be modeled as a web app are situations in which containers can help a lot. In the class of stuff that we do—in building platforms — containers and networking complicate that, and the benefits of containers don’t really materialize when execution can’t take place there. 

*Network Bounds and Product Management:* At SVDS, we might use Docker between each other for development. Then it would play the same role as a [Vagrant][10], for example. It should be said that one have to be strong at deploying microservices well ([general design principles][11]), before even thinking about how to isolate and decouple the functionality. In that sense, each team will need to have good explicit or implicit product management. 

From a performance standpoint, if 40 services are needed to load networking has to be incredibly robust. There are a lot of pings back and forth. 


*Additional link: [Pretty cool chart][12] I found on latency from Peter Norvig and Jeff Dean.*





[1]: http://prakhar.me/docker-curriculum/
[2]: https://www.docker.com/
[3]: http://www.informationweek.com/cloud/infrastructure-as-a-service/google-docker-does-containers-right/d/d-id/1319146
[4]: https://blog.codeship.com/why-docker/
[5]: https://store.docker.com/search?category=application_framework&source=verified
[6]: http://www.martinfowler.com/articles/microservices.html
[7]: https://plus.google.com/+RipRowan/posts/eVeouesvaVX
[8]: https://medium.com/aws-activate-startup-blog/using-containers-to-build-a-microservices-architecture-6e1b8bacb7d1#.yul4pgcng
[9]: https://technologyconversations.com/2015/11/04/docker-clustering-tools-compared-kubernetes-vs-docker-swarm/
[10]: https://www.vagrantup.com/
[11]: https://12factor.net/
[12]: https://gist.github.com/hellerbarde/2843375