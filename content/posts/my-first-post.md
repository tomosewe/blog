+++
date = "2018-01-25T18:35:32+13:00"
draft = false
title = "Setting up a blog with Hugo and Netlify"

+++

[Hugo](https://gohugo.io/) is a static site generator that claims to be the world's fastest framework for building websites. I've used [jekyll](https://jekyllrb.com/) in the past to set up a quick blog but found it clunky to use and the build time to be quite slow. So far Hugo has been really easy to set up. (apart from a few issues getting Hugo installed on Ubuntu correctly) I'm loving the huge amount of themes to choose from and switch between. 

Deploying a new Hugo site is also really easy. In the past I've used [GitHub Pages](https://pages.github.com/) and also [Firebase](https://firebase.google.com/) for hosting. However this time I've decided to use [Netlify](https://www.netlify.com/) as I've heard quite a lot of great things about it. 

I had a few hiccups getting it deployed. The first was solved by adding the public folder to my .gitignore file. When Netlify deploys your site you can set it up to run hugo and deploy the public folder. Having a public folder already set up can sometimes interfere with a new build.

The second issue I was that I needed to put the right url in the baseurl setting in the config.toml file. After deploying your hugo site the first time, rename the default url to something more appropriate and then add that url to your config.toml file. This makes sure that all your css and other assests are routed correctly. 

Ultimately it was a real breeze setting it up. I'm looking forward to blogging more this year with Hugo.



