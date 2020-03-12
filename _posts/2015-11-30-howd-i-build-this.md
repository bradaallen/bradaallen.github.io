---
layout: post
title: "How'd I build this thing?"
modified:
excerpt: "TL;DR: How to spend more time than is necessary on plumbing."
comments: true
tags: []
---

First, if you like this format (thanks!) you can download it from my Github page [at this link][1].
I built this site with a goal to: 

* use Github/Bitbucket and understand best practices
* play with HTML, CSS, and markdown
* get familiar with the AWS console

In terms of requirements, I wanted a place where I could share a bit of myself (eg, my photos) 
and document things I am working on. The site also should be clean and responsive to different
media - eg, just as comfortable on a tablet or a phone as a laptop. After $1,500 in refunds (I'll
explain below) and ~20 hours of cobbling different code together, I am feeling pretty good about 
where things are at. 

## Choosing a layout

Layouts are easy to download [via this Cloud Cannon website][2]. I first started with [Strata][3], which
I thought was beautiful and great on a phone, but could not figure out how to set a navigation
bar for non-blog-related items. I ended up settling on [Minimal Mistakes][4] since it had similar
functionality capabilities. 

For more involved instructions, [Jekyll RB][5] and [Jekyll.tips][6] were very helpful. More
work than what I am describing is likely - as an example, I had to download Ruby to get the 
gem package manager, etc.

## Setting up AWS

Once the layout is determined, it can be hosted on Amazon S3 for (basically) free. AWS is great 
as a starting point as well because it scales dynamically and has a [Free Tier][7] for the first 
year of use. One goal was to learn about the AWS Console - and just about anything can be done 
through it, from storage (S3) to computing (EC2) to different RDBMS, EDW, and NoSQL options. I am 
hoping to use their AWS IoT product for a home temperature sensing project I have.

To manage the syncing, [here is some very simple software and easy instructions][8]. There 
is some nuance on the AMZN side of this that is not very clear, however. Their instructions 
for this process [can be found through AWS][9]. A few highlights (things I initially did wrong):


1. Make two S3 buckets, **one with your root name and one with the "www." extension**
2. **Make sure that your `s3_config YML` file points to the `_site` folder.**
Otherwise, it will return the `index.html` file and there will be no rendering, etc.
3. **Have your server be somewhere in the US.** Originally, I thought it was cool to have my
site hosted in Tokyo or Buenos Aires or whatever- but actually, this just created extra work
in my `s3_config` file. So, if you go this route, make sure you're synced up in all of your files!
4. **Use AMZN for domain registration.** For networking, I bought my domain at [BlueHost][10] which 
is a cheap/not great place. I had to call to cancel hosting (couldn't do it online), I had to 
*opt-out* of additional services I didn't want, etc. I was generally unhappy - I also couldn't 
download any of the A or CNAME files, which AMZN suggested doing. Ultimately, I just had to point 
all of the nameservers to where they were hosted at AWS - but it wasn't a pleasant process. 
5. **NEVER post your private key online!** This may seem obvious, but I've learned the beauty of
`.gitignore` the hard way. Less than 12 hours after I originally uploaded my site to Github,
I received an email from AMZN that my key had been scraped and used to set up more than 150 EC2
instances around the world. I was being charged computing services at a rate of ~$2,800 a day.

<figure>
	<img src="/images/Not_Smart_Brad.png">
	<figcaption>Not smart, Brad.</figcaption>
</figure>

## Making modifications 

I don't have a sense of how the site will evolve, but I wanted to allow for the functionality
to upload photos, or create landing pages for events/dinners, etc. I've just created the photos
functionality, for now. I found two things I really liked:

1. [A Lightbox2 carousel][11]. This is a JQuery script that has the image "pop out" to a layer
above the original screen. All photos on the page can then be cycled through. I liked the code
(and the `for` loop that allowed the photos to be accessed through a `.MD` file), but didn't
like that [all of the photos were only in one column][12].
2. [Responsive image grids][13]. I think this is super cool - but the original code has the 
image files directly in the HTML, so that would need to be edited if I ever wanted to add photos.
Also, since my space for photos is the right 65% of any screen, I removed the option for a 4
column grid.

Mashing the two together - a Lightbox `_include` function, a `for loop` in the HTML file and a new
`photo.html` file in the `_layouts` folder sets up the site to its final state!

[1]: https://github.com/brad-svds/Apprentice
[2]: http://jekyll.tips/templates/
[3]: https://github.com/CloudCannon/Strata-Jekyll-Theme
[4]: https://github.com/mmistakes/minimal-mistakes
[5]: http://jekyllrb.com/
[6]: http://jekyll.tips/
[7]: https://aws.amazon.com/free/
[8]: https://github.com/laurilehmijoki/s3_website
[9]: http://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html
[10]: www.bluehost.com
[11]: http://christianspecht.de/2014/08/22/jekyll-lightbox2-image-gallery-another-approach/
[12]: http://jekyll-gallery-example.christianspecht.de/gallery-text2/
[13]: http://alijafarian.com/demos/responsive-image-grids-using-css/
