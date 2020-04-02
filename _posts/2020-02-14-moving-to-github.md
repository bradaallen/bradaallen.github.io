---
layout: post
title: "Moving hosting from AWS to Github."
modified:
excerpt: "Quick notes on setting up a gh-pages blog using Windows 10."
comments: true
tags: []
---

*This article was written in 2017 during my time at SVDS. The article was first published on the [SVDS Blog][0].*

*In the [introductory post][1], we walked through some examples of how SVDS has seen data capabilities determine the success of customer journey initiatives for our clients. In this post, we offer guidance on the data-related initiatives that you can start today to begin fostering closer ties with your customers—regardless of where you currently are in your specific state of development.*

GH Pages:1. Use WSL, don't mess with the devkits: https://kiazhi.github.io/blog/Working-with-Jekyll-and-Ruby-on-Windows-for-GitHub-Pages/#getting-started-with-jekyll-on-windows-10-using-windows-subsystem-for-linux
2. Use rbenv, don't mess with bare installations: https://brainwipe.github.io/jekyll/hyde/ubuntu/2017/05/16/pulling-jekyll-teeth/
3. Make sure you are using the gh-pages dependencies for Ruby and Jekyll: https://pages.github.com/versions/* if you had other versions pre-installed, make sure you are loading from rbenv (eg, the shims in ruby and jekyll)
4. Pick your theme; I like minimal mistakes: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
5. Follow this site for then creating your GH repo, testing locally, etc: https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll
6. Set up a custom domain, if desired: https://help.github.com/en/github/working-with-github-pages/configuring-a-custom-domain-for-your-github-pages-site
Don't forget the ~/.bashrc and . in jekyll new! rbenv init -, etc.
https://bryancshepherd.com/data-science/setting-bluehost-dns-github-jekyll-blog/  

https://help.github.com/en/github/working-with-github-pages/configuring-a-custom-domain-for-your-github-pages-site 
https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site
https://medium.com/@kimcodes/setting-up-a-web-page-with-github-pages-f77d45573ab2

[0]: https://www.svds.com/customer-journey-set-success/
[1]: https://bradaallen.github.io/customer-journey-success-part-1/
[2]: https://hbr.org/2015/11/competing-on-customer-journeys
