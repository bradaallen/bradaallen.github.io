---
layout: post
title: "True Agile: Core to a DS Workflow."
modified:
excerpt: "Or, 'how I got good at managing expectations under uncertainty.'"
comments: true
tags: []
---

*This article was written in 2017 during my time at SVDS. The article was first published on the [SVDS Blog][0].*

*In the [introductory post][1], we walked through some examples of how SVDS has seen data capabilities determine the success of customer journey initiatives for our clients. In this post, we offer guidance on the data-related initiatives that you can start today to begin fostering closer ties with your customers—regardless of where you currently are in your specific state of development.*

Include Tristan Handy stuff: https://blog.getdbt.com/4-questions-to-help-you-more-accurately-scope-analytics-engineering-projects/

Framing the approach: Data Science requires Agile & Product Management Skills

Agile develops products faster by acknowledging the current uncertainty in the final solution. In my workplan, I am trading time for information that helps me manage this uncertainty. 
At the beginning of a model's development, I don’t know:
The client’s preferred metrics for measurement
Business constraints that shape the necessary inputs/outputs
The right form factor that will ensure a tool is used
Any required changes to operational processes if a tool is not currently used (and associated resistance to change)
The greatest uncertainty should be “pulled forward” the farthest. Things that have material risk on the outcome should be (1) broken down into tests that (2) generate information that (3) allow for decision-making under greater certainty.
Acknowledging uncertainty is the key differentiator from an Agile and a waterfall process. The fact that my original plan could be wrong is the only reason iterations or adjustments are necessary. J
Erroneous assumptions can be very dangerous. If I assume a fact without designing a test, I am propagating the risk that I could be wrong “throughout” the project.

1. By having a solution-mindset, and by trying to define clear product and technical requirements - I can then build slices of functionality that allow me to iterate towards a final solution.
Establish an MVP and build complexity over time. Google's Rules of ML suggest starting after heuristics become too complex.
UI/UX and “core” (technical) functionality can be developed separately and in parallel. Each informs the other and is driven by usability. Looks like vs. Works like.
For UI/UX and systems design, design thinking is powerful. Particularly: 
Prioritizing visual tools (eg, wireframes, excel mockups) for feedback
Using user feedback to argue for change (BCG tool recommendations are made “on behalf of the user”)
Effective use of divergent + convergent thinking modes when brainstorming (called out to me by BCG Classics as a particularly powerful method)

Internal priority #1: Technical debt is a killer - need to trust the process.
Clean code really pays off - it reduces team velocity and makes it hard to create options
Code Spikes
Good PR process - complexity is added in small chunks. 
Sprint Goals need to be output driven. DS and SDS can have a tendency to be task oriented; it makes acceptance criteria less valuable and can lead to reduced productivity.
User Stories shouldn’t be more than 1-2 story points. Story Points are used to size work during sprints. They aren’t a tool to measure a developer’s productivity. User Stories shouldn’t bleed between sprints.
Have a Plan B that is viable. Creating options is what makes Agile work work well.

External priority #1: Communication in cross-functional teams is paramount
3. Keep high transparency with the business. Onboard them into the "back-office" work of model building and management.
	* They should know they are on a learning journey, and what we are finding together.
4. Always be clear - to everyone - on the definition of "done."
	* And what level of "done" is appropriate for the problem at hand.
	* A key client understanding is on the tradeoffs between flexibility and automation. 
5. Nobody should believe the model is a "black box."
	* Code is logic. If it can't be explained clearly, it's poor logic.
	* We have a lot of smart people - when we do this, we deny ourselves the opportunity for good feedback.
6. What makes this particularly challenging is how orthogonal DS is - and its heavy reliance on apprenticeship – both sides are gaining experience and may not have the language yet to communicate effectively. 

“Defining done” is a common source of frustration between Classics and Gamma. 
Eg, the difference between the same output but where the code is (1) a rough script, vs (2) functional/modular/parametric, vs. (3) tested, vs. (4) automated
https://www.oreilly.com/radar/lessons-learned-turning-machine-learning-models-into-real-products-and-services/

[0]: https://www.svds.com/customer-journey-set-success/
[1]: https://bradaallen.github.io/customer-journey-success-part-1/
[2]: https://hbr.org/2015/11/competing-on-customer-journeys
