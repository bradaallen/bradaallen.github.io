---
layout: post
title: "Setting up a Jekyll gh-pages site on Github."
modified:
excerpt: "Quick notes for easy setup if you have Windows 10."
comments: true
tags: []
---

When I first set up this blog, I knew I wanted to use a Jekyll layout - they're nice, responsive, and work well across devices and browsers. They also have nice coupling with Github, which should make serving easy and free. The problem was that getting Ruby and Windows to work well together weren't obvious (not much experience), and WSL had its own issues at the time - although promising. So, I set up the site to serve from AWS via S3 and wrote about that process [here][0]. 

&nbsp;<Enter> 

Good news - all of these challenges have now come a long way, and setting up everything locally and having GH do the work for you is super easy! So, I've moved from AWS back to Github. I also find that I am actually writing more now - calling `bundle exec jekyll serve` from the Ubuntu terminal is no sweat, and after a commit, the work is out there in less than 1m. There are a few minor things that tripped me up - documenting here to make easier for others. 

### Steps to getting your blog up on GH via Windows 10

1. **Use WSL and the Ubuntu terminal!** The Ruby devkits for Windows were known to be challenging - it required a **very** strong desire to make it work. I would [follow these directions][1] for getting WSL and bash set up on your terminal - but stop before it recommends downloading Ruby!! 
2. **Don't mess with bare installations, use rbenv.** This was [a good article][2] documenting `PATH` challenges when not using rbenv, as well as scripts for getting everything up and running. 
	* **When installing Ruby and Jekyll, make sure to use the gh-pages specified dependencies**: Link is [here][3]. If you had other versions pre-installed, make sure you are loading from rbenv (eg, the shims in ruby and jekyll)
3. **Create and initialize your GH repo.** Github has good instructions for this [here][4]. I made sure to have the bundler installed. 
4. **Pick your theme.** Github has a list of [supported themes][5] - these work out of the box, and are specified in your config file. Github also [supports remote themes now][6]. This requires a little bit of extra work, but expands the number of layouts you can use. I like and use [minimal mistakes][7]. 
5. **Set up a custom domain, if desired.** [Github has a good walkthrough][8], and many folks on the internet have worked through this themselves. Depending on where you buy your domain, each company has slightly different ways for managing the CNAME, A records, etc. I originally had been using bluehost and [found this guidance helpful][9].   
6. **Write your first post!** Your post will be in the `_posts` folder for the repo (which is created when you instantiate with `jekyll new`). The filename will be the date of the posting + the URL path for the post. For example `2018-05-02-setting-up-blog.md` will render as posted on May 2nd at your site: `xxx.github.io/setting-up-blog`. 

&nbsp;<Enter> 

I hope this is helpful. If you have any questions, thoughts, or comments - please let me know!

[0]: https://www.svds.com/customer-journey-set-success/
[1]: https://kiazhi.github.io/blog/Working-with-Jekyll-and-Ruby-on-Windows-for-GitHub-Pages/#getting-started-with-jekyll-on-windows-10-using-windows-subsystem-for-linux
[2]: https://brainwipe.github.io/jekyll/hyde/ubuntu/2017/05/16/pulling-jekyll-teeth/
[3]: https://pages.github.com/versions/
[4]: https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll
[5]: https://pages.github.com/themes/
[6]: https://talk.jekyllrb.com/t/remote-themes-on-github-pages/1214
[7]: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
[8]: https://help.github.com/en/github/working-with-github-pages/configuring-a-custom-domain-for-your-github-pages-site
[9]: https://bryancshepherd.com/data-science/setting-bluehost-dns-github-jekyll-blog/
