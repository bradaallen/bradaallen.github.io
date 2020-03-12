---
layout: post
title: "Data science programming for n00bies."
modified:
excerpt: "With so many things tying data science together... where to start?"
comments: true
tags: []
---

I have spent much of the past two years developing classes and seminars that highlight the
importance of data science, and generally how companies can make most efficient use of 
their own information. Now being in a position in which I can act on that, I am trying to
teach myself python so that I can be a more effective partner to the data scientists and 
engineers on the teams I am a part of. 

I should qualify that I am not starting *entirely\* from scratch; my undergraduate degree
had several courses in C+, and Arduinos use a similar code. So, I have an undeveloped 
intuition for state and object-oriented programming. At Stanford, I also took a statistics 
course that doubled as an introduction to R and SQL - which gave me a sense for how to 
visualize, clean, and transform data. 

At [SVDS][1], many of our scientists and engineers use python to do their data exploration (eg, with
the pandas, seaborn, scikit-learn, and numpy packages). So, even though the JHU Coursera course
is taught in R, I am going to try and recreate the same experience with python + pandas + Spyder
notebooks. With regard to time - I would estimate that all of this could be done between ~3 weeks
(if moving quickly, ~20 hours a week) to a few months. 

## First, Get the New Gear!

It's important to make sure you've got all the necessary requirements to 
use the force. One does not simply become a jedi. 

<figure>
	<img src="/images/squad_new_gear.jpg">
	<figcaption>What it feels like downloading new packages.</figcaption>
</figure>

* **Python:** See if you already have it installed by going to your terminal and typing "python". 
If that doesn't work, you can download a version [at this link][2]. I was recommended to use 2.7, but there
are later versions of Python 3.
* **Package Managers:** These puppies help ensure that the different software tools you download have consistent
dependencies. [Anaconda][3] is a popular one for Python, [pip][4] is also used, and a lot of folks in my office 
use [homebrew][5] for OSx
* **Check for Packages:** If you want to see what packages you have, you can go into your terminal and
enter the command `conda list` (for Anaconda) or `pip list` - you'll see both the package and the installed version. 
Each of these packages have sets of functions you might want to use later - the code is already written for you, so
you can just call it and let it do the work for you. 
* **Git:** [Git][6] is a place where you can do version control on your software, and share personal projects. It's great
for a few reasons: 
	* Similar to how packages are used - when you are working through a specific problem, you can search git 
to see if someone else might have already posted their solution or find different ways people have tackled
what you are trying to do. 
	* It also is efficient for managing collaborative teams - projects have a "master branch" that represents the most recent official version, and "forks" in which people can work on improving
pieces of the code separately.
* **Spyder:** [Spyder][7] is a development environment that is helpful for managing dataframes and visualization. There
is an area for text editing, a console for computing, and visualizations are easy - it is very similar in
look and feel to RStudio. 
* **Jupyter/iPython Notebooks:** [Jupyter][8] notebooks are great de facto "lab notebooks" for doing exploratory
work. I could write about why they are great, or you could take [my colleague Jonathan's opinions][9] on why it is good for him.
* **Sublime Text:** Finally, [Sublime Text][10] is a pretty common text editor that many folks in my office use. They have
thoughts about why it is better than other text editors. Lots of packages, ease of use, etc. I'm using it primarily because most
others do. Learn Python the Hard Way, for example, recommends Text Wrangler. 

## Learn Python the Hard Way (~Class 1-28)

If your plan is to be self taught, [Learn Python The Hard Way][11] is a good place to first dip one's toes into 
programming. The *best\* start is to have a project that would require use of python (and 
there are plenty of these online), but I keep finding a "chicken and egg" problem: the more 
I learn about different libraries, packages, and functions, the more utility I see in the 
language. That intuition is difficult to develop without at least some guided instruction.

I highlight the first half of the class because it is very basic, and moves at a speed that
is different than the second half of the course. Zed Shaw, who developed the program, gives
guidance on: 

* how to use the command line, 
* how to download and install all of the programs,
* what to look for in a text editor, and 
* thoughts on preliminary debugging techniques

By the end of ~Class 28, you know how to execute a script and lists, dicts, and tuples are
starting to become part of your vocabulary.

## Google's Python Class

[Google's class][12] is scheduled to be performed over two days, and is recommended for folks with 
prior programming experience. I found that the logic from the first half of LPTHW was sufficient
enough for me to make use of their course. Also - it actually does only take two days, with
maybe 10 hours of work in total. 

The first day covers some building blocks of python: strings, list, sorting, and dicts/files.
There is some code around `for` loops and how to build/manipulate data structures (eg, the `append`,
`extend`, `pop` functions, etc). It is a good complement to LPTHW in that it is well structured and
the exercises are more exploratory (and the solution scripts are provided), so you can get 
stuck/challenged and have to find your way out, but not struggle too much if you don't want to.

The second day focuses on the regular expressions function and utility modules (eg, `os`,
`os.path`, `shutil`, etc). This builds towards an exercise called "Baby Names" in which the user
takes scraped HTML data and pulls out the ranking of baby names for a given year - for example,
"Michael" was the "#1" name for "boys" in "1990." It's some pretty gnarly and powerful code.
Getting one character wrong in the example below would result in a completely different result.

Seriously, check this out:

	# each tuple is: (rank, boy-name, girl-name)
	tuples = re.findall(r'<td>(\d+)</td><td>(\w+)</td>\<td>(\w+)</td>', text)
	#print tuples

The second exercise focuses on pulling, managing, and creating external files, which can be useful
for cleaning file structures. The user is asked to look for files that have the pattern "__XXXX\_\_" in
the filename and then move and zip them to a different directory. 

Having an exercise that dealt with scraped HTML data also gave me an appreciation for the 
"level of mess" one might be asked to deal with in their data - many of the other python exercises 
I've performed were around the logic of the code and transforming it to support a regression or 
classification. As a result, the data started in a relatively ordered CSV file, and my ask was to
label, encode, or bin the data - not to create the entire underlying structure myself. 

Ultimately, I found that the class showed how python can be used as a tool - a lightweight, quick
solution to cleaning up and working through messy data. There was not much higher order structure,
or any discussion of developing unit tests to support the code. I left the two days seeing python
almost as a scalpel that is part of a broader toolkit. 

## Learn Python the Hard Way (~Class 28+)

The second half of LPTHW is significantly more advanced than the first - it incorporates the
logic of object-oriented programming, and introduces the concepts of inheritance and composition.
It also shows how to make code more robust, by using nosetests / writing unit tests, and establishing
a basic file structure for more complex projects. 

In this regard, I found it to be *significantly* different than Google's Python Class; I think the
lack of overlap means the two parts complement each other well. Together, they gave me a sense of how to 
establish robust code, how to build towards scale, but also the practical skills of cleaning and 
file manipulation. It gave me a good basis to determine what might be good future projects for my learning.

As a separate note: had I not had state programming beat into me, I would have found the second half of LPTHW
to be very challenging and would have required a lot of time and practice to adopt their principles. I'm 
using it as guidance for projects I might want to take on in the future, and it has been very helpful in 
being able to ask my colleagues if I can see their code (and what I should be looking to understand
around how they think about developing).

## pandas + Data Weekends

Tying everything together, I took a tutorial of the [pandas package][13] (it says 10 min, it's more like 2
hours) and then took my friend Francesco's weekend machine learning workshop, [Data Weekends][14]. Francesco
is a great teacher; he was a PhD in Physics and most recently was the Chief Data Officer for a Y-Combinator
start-up, [Spire][15]. 

Francesco's course was really useful. He organized the two days into four types of analysis - clustering,
regression, classification, and dimensional reduction, and based this on the nature of the data and the outcome one
wants to achieve (that is, supervised or unsupervised learning and is the use discrete or continuous). 

We then went through a variety of different models one could apply (eg, K-Nearest Neighbors, LASSO, Trees,
Random Forest, Decision Classifiers, Logistic Regression, K-Means Clustering, etc), the associated packages
(eg, scikit-learn), and how to structure the information in a way that allows for the analysis (eg, general
cleaning, labeling, etc.)

It was great to get to work through real code, to struggle with getting the python syntax and imports correct,
and to have advanced/extension activities in iPython that guided me to new applications and allowed me to practice
myself. We finished the day by creating an application that tries to detect the language one is using when 
entering a random prompt. [I set up the application on Heroku using Flask][16].

<figure>
	<img src="/images/Heroku_App.png">
	<figcaption>Machine Learning at its finest.</figcaption>
</figure>

## Understanding Best Practice and Other Useful Programs?

Going forward, my hope is that I am in a position in which I can learn best practices from [the folks I work
with][17]; they're kind enough to deal with my questions, provide advice, and share with me some of their code that
shows how they've thought though novel problems or worked through particularly thorny challenges. 

I've also catalogued a few great data sources for coming up with my own personal problems: 

* the [US Government][18] (nice!),
* [UCI's Machine Learning repository][19], 
* [Reddit's datasets archive][20], and 
* [100 interesting data sets for statistics][21]

For staying in the loop with the latest goings on, I've found [Data Elixir][22] and the [Partially Derivative][23]
podcast to be pretty awesome. I'd love to hear any thoughts or suggestions others might have, though -
both with regard to interesting projects as well as great things to read!


[1]: www.svds.com
[2]: https://www.python.org/downloads/
[3]: https://www.continuum.io/downloads
[4]: https://pypi.python.org/pypi/pip
[5]: http://brew.sh/
[6]: https://github.com/
[7]: https://pythonhosted.org/spyder/
[8]: http://jupyter.org/
[9]: http://www.svds.com/jupyter-notebook-best-practices-for-data-science/
[10]: http://www.sublimetext.com/
[11]: http://learnpythonthehardway.org/book/
[12]: https://developers.google.com/edu/python/?csw=1
[13]: http://pandas.pydata.org/pandas-docs/stable/10min.html
[14]: http://www.dataweekends.com/
[15]: https://www.spire.io/
[16]: http://salty-inlet-1328.herokuapp.com/
[17]: http://www.svds.com/about/
[18]: http://www.data.gov/
[19]: http://archive.ics.uci.edu/ml/
[20]: https://www.reddit.com/r/datasets
[21]: http://rs.io/100-interesting-data-sets-for-statistics/
[22]: http://dataelixir.com/issues/63?#start
[23]: http://www.partiallyderivative.com/