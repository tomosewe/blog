---
title: "Updating Netlify Environment Variables"
date: 2019-07-09T22:35:08+12:00
draft: true
---

For my last blog post, the usual push to `master` wasn't deploying my site to [Netlify](https://www.netlify.com/).

My first port of call was to take a look at the build logs in `Netlify` itself.

![Failed deploy message](failed-deploy.png)

Aha! Let's have a look at the logs. This line looks interesting.

![Wrong version message](wrong-version.png)

Looks like we're somehow using an older version of [Hugo](https://gohugo.io/) than our theme supports.

Let's have a look at the environment variables

![Environment variables panel](env-variables.png)

Looks like we set it to `0.34` when we first set up the site. Let's update it to the latest version.

![Entering new versoin](new-version.png)

Now let's trigger a new deploy.

![Trigger new deploy](trigger-deploy.png)

It worked!

![Deploy success](deploy-success.png)
