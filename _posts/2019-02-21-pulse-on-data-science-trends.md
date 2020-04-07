---
layout: post
title: "Review of recent trends in Data Science."
modified:
excerpt: "Topics: data engineering, role definition, project management, experimentation, et al."
comments: true
tags: []
---

*Every week, I spend ~5h reading my favorite newsletters on data science (eg, Data Science Roundup, Data Elixir, Jack Clark, Daniel Meissner). My most recent project prevented me from catching up on these articles for a few months - so I took a few days to catch up and synthesize what I had been seeing. That summary can be found below.*

### Key takeaways

Most of the interesting articles were saying the same things:
1. Role definition is still happening, but there is alignment that hybrid models in business are useful
2. Businesses are continuing to invest in these initiatives, more understanding that it is not “magic”
3. Platforms and cloud tooling continue to enforce the imperative for DS to be able to own models “end to end” - the DS needs to write clean code and launch to production; can be on platforms built by SWE & DE
 
I didn’t see very much interesting on actual techniques ([besides a very interesting post on transfer learning as deep feature extraction][0]), but have shared some below. Lots of talk on ethics, some talk on RL and all of the NLP stuff (Bert & ELMo, etc – great summary of this as an ImageNet moment [here][1]). 
  
### Role of a Data Engineer

[Do I need a data engineer?][2] Here is a second article, [distinguishing between DE and an “Analytics Engineer.”][3] Suggests using stitch, fivetran, dbt as data engineering tools in lieu of Airflow. Natural migration (in startups at least) is to do PoCs, early builds on Airflow and then migrate to a more resilient tool like those listed. Super critical role (and primary responsibilities of our principal data engineers on a project), should be responsible for:
* Managing and optimizing core data infrastructure,
* Building and maintaining custom ingestion pipelines,
* Supporting data team resources with design and performance optimization (think 1 DE for 3 DS) and
* Building non-SQL transformation pipelines (PySpark ETL (maybe), geo enrichment)

I thought the idea of removing Airflow for SQL transformations was an interesting trend. I haven’t ever used the three “pipeline-as-a-service” products. For my own projects, the above responsibilities were good to have for our primary data engineer, with a separate, proper SW developer as the code master. 
 
### More on role definition. [“The Kinds of a Data Scientist.”][4]
* The VP, DS of Instacart [split the key types of work][5] into “Decision Science” vs. “Data Products” to identify skills required. I thought the Decision Science example was pretty interesting.

> *At LinkedIn, the executive team used decision science to make a critical business decision about the visibility of member profiles in search results. Historically, only paid users could see full profiles for everyone in their extended (third-degree) network. The visibility rules were complex, and LinkedIn wanted to simplify them — but not in a way that would undermine its revenue. The stakes were enormous. 

> The proposed visibility model was a monthly use limit for unpaid users, with a cut-off based on usage. LinkedIn’s decision scientists simulated the effects of this change, using historical behavior to predict the impact on revenue and engagement. The analysis had to extrapolate past behavior on one model to forecast behavior on a radically different one. Nonetheless, the analysis was sufficient to move forward.* 

* [“Code as Configuration”][6]. Article written by an experienced DS outlining how DS & SWE/DE should think about working together.
 
### Project management.
* [Doing Agile in Data Science][7]. Google. Particular focus on taking the scientific method and breaking it down into “less rigorous hypotheses” that can be (1) time bound and (2) better inform the LT hypotheses you want to prove or disprove in an experiment.
* [Divergent and convergent thinking in data analysis][8]. An okay article, on a great concept. With the article above, how do we coach projects to (1) generate good hypotheses with the associated code “spikes”, (2) then fit that into design patterns, etc. that allow us to grow code safely? This can also be very useful for identifying product/project/pilot requirements with business users. I’ve received feedback in projects that “divergent thinking is very uncomfortable” but the decisions it can lead to are almost always of higher value than what a convergent path would provide.
* [Design for Continuous Experimentation][9]. Etsy. How Etsy learned to build stage gates into their product development process and use A/B tests to enable stage gate decisions (!!!) I liked how the Principal Engineer framed the way they used their learning from things that did not go well for future projects
* [How much should managers code? Wrong question. Where to write code?][10] Coursera. Emphasizes being invested in small bug fixes, code reviews, and JIRA to develop a manager’s empathy for the team’s work and foster better outcomes.
* [The State of Data Product Management Roles][11]. Insight Data Science. Highlights 5 domain areas: Infrastructure, Analytics, Applied ML/AI, Platforms, Standardization & Discovery. Note that Analytics and Applied AI/ML roles map well to the two different “kinds of data scientists” outlined above, and the other 3 are DevOps-y in nature.
 
### Experimentation.                    
* [Guidelines for AB Testing at Etsy][12]. Advocates for frequentists methods and to establish measurement up front first. Great anecdote on how more measurement up front changed their delivery process for new features. Many, many links for follow on reads.
* [Is Bayesian Testing Immune to Peeking? Not Exactly][13]. Stack Overflow (the company). Less about the Bayesian approach, I thought this was a great way of showing how to use simulation to trust the data behind your decisions (and how p-values can change over time). I fell into a small rabbit hole reading about AB testing from these articles; a theme for me was many different teams using simulation to “shore up” questions around experiment design.
* [Analyzing Experiment Outcomes: Beyond ATEs][14]. Uber. Walks through a metric called Quantile Treatment Effect (QTE) that allows for understanding heterogeneity in treatment effects. Cool.
* [Experimentation & Measurement for SEO][15]. Airbnb. Useful case study of when to use differences-in-differences and some of the idiosyncrasies to account for.
 
### Data / infrastructure engineering.
* [Capturing data evolution in a SOA][16]. Airbnb
* [Putting the power of Kafka into the hands of data scientists][17]. Stitch Fix
* [Future of Data Warehousing][18]. Cloudera/PNC. Short, 5 min video outlining some challenges standing up a distributed system – seen these challenges at all projects and would expect our DE to work with and help the client set up these processes.
 
### Techniques, Tools, & Interesting reads.
* [Contextual bandits for content outreach][19]. Stitch Fix
* [How to write clean code and conduct code reviews][20].
* [Forecast sales in retail][21]. A good reference for establishing a baseline and packages/methods
* [3 facts about time-series analyses that can surprise ML people][22]. (eg, “The uncertainty of the forecast is just as important as, or even more so, than the forecast itself.”)
* [11 classical time series forecasting methods in Python][23]. Related: [Forecasting at Uber][24]. Interesting to see Uber’s built-in backtesting system.
* [A short history of prediction serving systems][25]. RISE Lab. Discusses the architecture of RISE’s Clipper system, and has an interesting paper from LinkedIn on managing the tradeoff between accuracy and serving latency.
* [Papermill][26]. Parametric, scheduled Jupyter notebooks with the option for aggregate summaries. Used a lot at Netflix.
* [Convoys][27]. PyPI package for time-lagged conversion rates (eg, telco churn..)

[0]: https://www.basilica.ai/blog/the-unreasonable-effectiveness-of-deep-feature-extraction/
[1]: https://thegradient.pub/nlp-imagenet
[2]: https://blog.fishtownanalytics.com/does-my-startup-data-team-need-a-data-engineer-b6f4d68d7da9
[3]: https://www.locallyoptimistic.com/post/analytics-engineer/
[4]: https://hbr.org/2018/11/the-kinds-of-data-scientist
[5]: https://firstround.com/review/doing-data-science-right-your-most-common-questions-answered/
[6]: https://www.locallyoptimistic.com/post/code-as-configuration/
[7]: https://hackernoon.com/rethinking-fast-and-slow-in-data-science-b2ce18d5b054
[8]: https://simplystatistics.org/2018/09/14/divergent-and-convergent-phases-of-data-analysis/
[9]: https://www.youtube.com/watch?v=qCKj_K5RNfY
[10]: https://medium.com/coursera-engineering/should-engineering-managers-write-code-wrong-question-ec5fc54d3903
[11]: https://blog.insightdatascience.com/an-introduction-to-the-data-product-management-landscape-ef930afe6de5
[12]: https://hookedondata.org/guidelines-for-ab-testing
[13]: http://varianceexplained.org/r/bayesian-ab-testing/
[14]: https://eng.uber.com/analyzing-experiment-outcomes/
[15]: https://medium.com/airbnb-engineering/experimentation-measurement-for-search-engine-optimization-b64136629760
[16]: https://medium.com/airbnb-engineering/capturing-data-evolution-in-a-service-oriented-architecture-72f7c643ee6f
[17]: https://multithreaded.stitchfix.com/blog/2018/09/05/datahighway/
[18]: https://www.oreilly.com/ideas/the-future-of-data-warehousing
[19]: https://multithreaded.stitchfix.com/blog/2018/11/08/bandits/
[20]: https://robatwilliams.github.io/decent-code/
[21]: http://exxeta.github.io/2018/10/forecast_sales_in_retail
[22]: https://towardsdatascience.com/3-facts-about-time-series-forecasting-that-surprise-experienced-machine-learning-practitioners-69c18ee89387
[23]: https://machinelearningmastery.com/time-series-forecasting-methods-in-python-cheat-sheet/
[24]: https://eng.uber.com/forecasting-introduction/
[25]: https://rise.cs.berkeley.edu/blog/a-short-history-of-prediction-serving-systems/
[26]: https://github.com/nteract/papermill#usage
[27]: https://better.engineering/convoys/
 
