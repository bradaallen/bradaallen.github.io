---
layout: post
title: "Analyzing NYC high school graduation rates."
modified:
excerpt: "Seeing what things were like when I was teaching."
comments: true
tags: []
---

###What was the assignment?

I recently built [a quick web application][1] to visualize New York City graduation rates for different cohorts and demographics. 

<figure>
	<img src="/images/ddp.png">
	<figcaption>Exploring NYCDOE graduation rates.</figcaption>
</figure>

This “data product” was an assignment for [Johns Hopkins data science course][2]. We were given the opportunity to choose our own datasets for analysis; I found the NYCDOE (Department of Education) graduation rates and immediately knew I had to use it. It was the data for NYC students at the same time I taught high school!

I taught physics and chemistry at the [High School for Global Citizenship][3] in Crown Heights, Brooklyn between 2007 and 2009. I had the pleasure of getting to work with the first two graduating classes of the school. However, I haven’t had much interaction with education in New York since, aside from working with a few education-focused non-profits.

###What is the product?

The website is dynamic, and allows for a user to view graduation rates for a given “cohort” of students. A cohort represents the year that a child entered 9th grade; this allows for the city to calculate 4- and 6-year graduation rates. These charts represent 4-year graduation rates for a given cohort.

I pulled the information from [data.gov][4]. A user can see the differences in graduation rate by borough, gender, race, disability, or ESL (English as a Second Language). The data is provided in an aggregation (ie, not on an individual student level) and therefore smaller cuts or permutations are not available.

Doing some experimentation with the charts, it is clear to see that graduation rates increasing across the board over the 5 years of data. There are also some challenging statistics. For example: 

* Only 20-40% of ESL students graduate in 4 years. 
* The graduation rate for special education students in the Bronx in 2005 (2001 cohort) was less than 15%. 
* There is almost a ~20% gap in graduation rates between Whites and Hispanics.
* There is a ~15% gap between females and males. 

In good news, though, these positive trends have continued through to the present: in 2015, the [graduation rate topped 70% for the first time ever][5].

###So, what did I learn? 

This was a fun product. I was happy to go back to the old school’s website and see how it has been doing, and it was good to think about my old students. The exercise also helped reinforce the benefits of good visualization; I’ve always appreciated the interactive designs of the NYTimes, for example, it was fun and instructive to think about how I wanted to structure an experience for another user. It was also good to get some more practical experience with basic web application frameworks, and setting up the server/UI code.

[1]: https://bradaallen.shinyapps.io/ddp_project/
[2]: https://www.coursera.org/specializations/jhu-data-science
[3]: http://www.hs-gc.org/
[4]: www.data.gov
[5]: http://www.nytimes.com/2016/01/12/nyregion/new-york-citys-high-school-graduation-rate-tops-70.html