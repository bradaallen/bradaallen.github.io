---
layout: post
title: "Data Science needs Agile and Product Management."
modified:
excerpt: "Or, 'how to manage expectations under uncertainty.'"
comments: true
tags: []
---

Over the last 5 years, I have led directly or been involved in a number of enterprise projects to introduce or expand the use of machine learning. As a Product Manager turned Data Scientist, I have found time and time again that many concepts in Product Management and Agile development help de-risk and enhance the overall effectiveness of ML solutions. 

In this article, I’ll highlight two key concepts - one from Agile and one from Product Management - and explain how they help build sustainable, reproducible ML systems.

### 1. Agile planning is about managing uncertainty - you are trading resources (eg, time) for information. Data science explorations adopt this mode of thinking well.

Acknowledging uncertainty is the key differentiator from an Agile and a waterfall process. The only reason I might need to adjust my backlog or iterate my sprint plans is due to the fact that my original plan could be wrong. Things **where being wrong hurts the most** should be (1) broken down into tests that (2) generate information that (3) allow for decision-making under greater certainty.

> “If it hurts, do it more frequently, and bring the pain forward.” - Jez Humble

In my projects, we call this aspect of project design “bringing the pain forward.” This is a concept from Jez Humble’s book on [Continuous Delivery][0]. His book focuses on automating deployment pipelines (testing, environment management, builds, etc.) to allow for more frequent pushes to production. However, the concept translates to more general risk management as well.

A primary goal is to eradicate [“toil”][1] - work that doesn’t make a meaningful contribution to the final product. Agile planning for ML models and applications follows a similar logic - seek to eradicate incorrect lines of inquiry, model choices, UI, and technical design as quickly as possible. 

Aspects of the plan that are not tested are assumptions. Erroneous assumptions can be very dangerous. If I assume a fact without designing a test, I am propagating the risk that I could be wrong “throughout” the project. 

Even benign assumptions can kill the value proposition of a solution, so it’s important to treat them with respect. For example:

* You do a small scale POC on one country’s transaction data using pandas or R. You know that scaling may require a centralized architecture and a distributed system, but you don’t have this discussion until you’ve proven your toy model’s efficacy. In discussing next steps, it becomes apparent your “value” is theoretical - the technical resources do not exist.
* You are working to optimize the pricing of in-store goods. Designing an A/B test is difficult - you have a policy of consistent promotions (eg, no holdout) within a state or country to manage against [complicated promotional pricing regulations][2]. You attempt to [design a difference-in-differences or synthetic control method][3] to prove incrementality, but the business sponsor dismisses it as theoretical. You have a conviction you’ve created value, but challenges in proving it.
* You are working on a classification problem, e.g., churn. The business user has sold a UI in which every customer has accurate probability predictions and clear rationale supporting each customer’s prediction. However, [low incidence rates (~1%) make probability calibration a challenge][4], and the range and nature of churn reasons makes [feature engineering for useful SHAP values][5] costly and difficult. Had you been involved earlier, you would focus on ranking/discrimination and decoupling rationale from prediction, if possible. 

At the beginning of a ML exercise, make a list of everything that can go wrong - and use that as a starting point for your planning!

### 2. Data science plans and assumptions are best managed when framed around a set of product and technical requirements. 

Notice above that I mentioned Agile tests are for *“where being wrong matters most.”* Experience and judgement really can make the difference between a successful project that completes on time and something that never quite works. Part of leading successful teams requires [building reserves of trust][6] with your team, your partners, and stakeholders.

A good way to build trust is to give a clear conception of the end solution, with a draft set of product and technical requirements. It should be clear that these requirements are assumptions and subject to revision. It is helpful to communicate which requirements have greater uncertainty, and their associated tests in the plan. 

For example, at the beginning of a model and/or application's development, I may not know:
* Any **required changes to operational processes** necessary for adoption (and the associated resistance to change)
* **Business constraints** that shape the necessary inputs/outputs - for example, pricing ladders constrain price outcomes, data loads/availability can affect scoring cadences
* The **right form factor** that will ensure a tool is used
* The **preferred business metrics** for measurement 

By having a solution-mindset, and by trying to define clear product and technical requirements, I can then build slices of functionality that allow me to iterate towards a final solution. 

A useful mental model for how to decompose a problem is shown by the [“looks like” vs. “works like”][7] approach to prototyping. In this approach, the UI/UX of a solution (the “looks like”) and its core functionality (the “works like”) can be developed separately and in parallel. As feedback about each component is collected, it may influence the requirements of the other component. For example, technical limitations may impact requirements for the user experience, and revisions of the user workflow may change the roadmap/priorities of the different technical features.

Each component of the overall solution can then be further decomposed into basic components, with a priority for collecting quick feedback. This follows John Gall’s famous [quote][8]: *“A complex system that works is invariably found to have evolved from a simple system that worked.”*

#### A few recommendations for building out your ML solution:

* For the solution design, the first simple system should be a [“walking skeleton.”][9] Having a functional end-to-end pipeline with limited functionality will ferret out any integration issues early, and can surface necessary storage and processing patterns.
* For the model design, the first simple system should be the quickest MVP that creates a baseline prediction. [Google's Rules of ML][10] suggest using ML only after heuristics become too complex. This logic should extend to ML solutions as well, starting with straightforward implementations that become increasingly sophisticated (eg, start with classical time-series methods for forecasting before testing nonlinear approaches). 
* For interaction design, design thinking approaches should guide the first simple system: 
	* Generate options for yourself - [get comfortable exploring ideas using divergent thinking][11]. Great solutions often steal components from multiple good ideas. 
	* Find ways to [collect user behavior][12] - information through engagement can often be of higher quality than basic market or user research.
	* Get engagement through visual tools (eg, [wireframing][13], excel mockups) - take time to listen and pay attention to points of friction or counterintuitive (to use) usage

### Applied ML - managing the “high risk, high reward” tradeoff.

ML systems are known for the tremendous value they can create, as well as their potential for [“high interest” technical debt][14], drift, biased predictions, etc. These challenges are often coupled with the need to educate business users on how to interact with such systems, their role and responsibilities, and managing expectations about what can vs. what cannot be done. 

Proven software development approaches for doing this well - particularly Agile and Product Management principles - can create trust and accelerate the adoption of these tools and capabilities.  

[0]: https://www.amazon.com/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912
[1]: https://landing.google.com/sre/sre-book/chapters/eliminating-toil/
[2]: https://risnews.com/promotional-pricing-right-side-law
[3]: https://arxiv.org/pdf/1610.07748.pdf
[4]: https://www.svds.com/learning-imbalanced-classes/
[5]: https://christophm.github.io/interpretable-ml-book/shap.html
[6]: https://blog.getdbt.com/4-questions-to-help-you-more-accurately-scope-analytics-engineering-projects/
[7]: https://www.hackster.io/news/starting-with-one-1f0ab62cbed4
[8]: https://quotesondesign.com/john-gall/
[9]: https://codeclimate.com/blog/kickstart-your-next-project-with-a-walking-skeleton/
[10]: https://techdevguide.withgoogle.com/resources/rules-of-ml/
[11]: https://www.teachthought.com/critical-thinking/3-modes-of-thought-divergent-convergent-thinking/
[12]: https://www.wired.com/2014/02/stanford-class-taught-two-normal-guys-star-designers/
[13]: https://www.experienceux.co.uk/faqs/what-is-wireframing/
[14]: https://research.google/pubs/pub43146/
