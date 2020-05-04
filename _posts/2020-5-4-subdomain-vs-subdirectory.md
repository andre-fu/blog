---
layout: post
title: Subdomain vs Subdirectory for hosting Jekyll as a subsite on github pages
---

Over the course of 3 days I struggled to figure out how to add this blog to my main website. In fact if you go to the commit history on `andre-fu.github.io` site you can see me struggling to figure it out! 

### First attempt

I had originally wanted to set jekyll up as a subfolder onto the main site like `andrefu.ca/blog` which would act as it's own autonomous subsite. The problem with this is ... Jekyll ... It doesnt play nice with an additional static site. 

I had moved the `_config.yml` file to my main `andre-fu.github.io` directory, but that didn't end up being useful because as I fooled around with the `baseurl`, `source`, `destination` none of it worked effectively. 

Scraping the internet, I found a variety of sources that were all quite frankly, useless. Especially [this stackoverflow post](https://stackoverflow.com/questions/48734528/jekyll-static-site-generation-on-a-subsite) somehow everyone kept referencing this post but honestly not useful.

In the end it ended up rendering without the `_sass` even after specifying the `sass_dir` folder in the config. The css wasn't not only not being converted, but also didn't effectively get compiled into css to be launched in `_site`. 

## The main problems

There are a few main problems I think that I encountered while trying to solve this problem. The main one being having to integrate jekyll into an existing github pages account. Since gh-pages tracks the master branch of that repo I'm not allowed to have more than one `index.html` file. Furthermore since gh-pages sees the `_config.yml` I think it thinks that its loading a jekyll site and gets confused about which index to load. Finally, I still don't know why the CSS breaks & the sass doesn't get converted. 

## Solution

Relatively easy: just make a new directory & add it as a project site with a subdomain instead of as a subdirectory. [In this SO post](https://stackoverflow.com/questions/50882264/get-jekyll-to-work-with-existing-github-pages-site?rq=1) they explain that serving it as a subdirectory is so much more complicated than what I had originally thought. 

In essence the subdomain gets treated as it's own unique site & you can link it from your main webpage. 

