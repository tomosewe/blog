---
title: "Setting up a blog with Hugo and Netlify"
date: 2018-01-26T18:35:32+13:00
draft: false
---

[Hugo](https://gohugo.io/) is a static site generator that claims to be the world's fastest framework for building websites. I've used [jekyll](https://jekyllrb.com/) in the past to set up a blog but found it clunky to use and the build time to be quite slow. So far Hugo has been really easy to set up and I'm loving the huge number of themes to choose from and how easy it is to switch between them.

Deploying a new Hugo site is also really easy. In the past I've used [GitHub Pages](https://pages.github.com/) and also [Firebase](https://firebase.google.com/) for hosting. However this time I've decided to use [Netlify](https://www.netlify.com/) as I've heard quite a lot of great things about it.

This post should serve as a quick tutorial for getting yourself set up with a new Hugo blog hosted on Netlify.

1. #### Install Hugo.

    For me this was on [Ubuntu](https://www.ubuntu.com/) so I'll go into detail for that. If you're using a Mac or Windows or another Linux distro, head to the [official installation page](https://gohugo.io/getting-started/installing/) and follow the instructions there. You can skip over to the next section once you're up and running.

    The official instructions say to use `sudo apt-get install hugo` but I found that the version was old and some themes no longer worked with that version. Instead I used `snap install hugo` to get the latest version. However, I then had to use the command `snap run hugo` whenever I needed to use Hugo, so I created an alias `alias hugo="snap run hugo"` to make things a bit easier. Run `hugo version` to make sure you're using the most recent version available, at the time of writing the most recent version is _0.34_.

2. #### Create a new site.

    In your terminal, navigate to the parent directory where you want to store your new site. Run `hugo new site blogtutorial`. This will create a new directory containing all the scaffolding required for your new Hugo site.

    ![hugo-new-site][hugo-new-site]

3. #### Choose a theme.

    Hugo has a [huge range of themes](https://themes.gohugo.io/) to choose from, or you can create your own if you prefer. I've gone for the [Hyde](https://themes.gohugo.io/hyde/) theme for this blog so we'll use that for this tutorial. Install the theme in your _themes/_ directory.
    ```bash
    cd themes
    git clone https://github.com/spf13/hyde.git
    ```
    Then add the theme to your _config.toml_ file by adding the line
    ```yaml
    theme = "hyde"
    ```
    at the top of the file.

4. #### Create your first post.

    Run `hugo new posts/my-first-post.md`. This will create a new file in _content/posts/_ named `my-first-post.md`. Go ahead and edit that file with some dummy content.

5. #### Build and run.

    Run `hugo` to build your site. Hugo will generate the site inside the _public/_ directory. Now run `hugo serve -D` The -D flag is to enable drafts. Your site will now be viewable on [http://localhost:1313/](http://localhost:1313/).

And that's it, you're set up with Hugo. Check out the [Hugo docs](https://gohugo.io/documentation/) for more in depth information.

Now it's time to get our site deployed to Netlify.

1. #### Push your site to GitHub

    Set up a Git repository on GitHub and push your new Hugo blog to the repository.

    > Tip: add your _public/_ directory to your _.gitignore_ file.

    > You won't need it as Netlify will run the `hugo` command and generate the folder for you.

2. #### Set up Netlify

    Head over to [netlify.com](https://www.netlify.com/) and sign up if you haven't already.
    Once you're all signed up, head to [app.netlify.com](https://app.netlify.com/) and click on `New site from Git`. Here you can link your GitHub account and choose your new blog repository.

    ![netlify-create-a-new-site][netlify-create-a-new-site]

    Choose to deploy your master branch. Set the build command to be `hugo` and the public directory to `public`

    ![netlify-deploy-settings][netlify-deploy-settings]

    Click on the `Show advanced` button. We're going to add a new key to make sure that Netlify uses the latest version of Hugo to build our site. Enter `HUGO_VERSION` as the key and `0.34` (or the current latest version of Hugo) as the value.

    ![netlify-advanced-build-settings][netlify-advanced-build-settings]

    Hit the `Deploy site` button and your site will be live!

The first time you view your site from Netlify you may notice that none of the styling is working. This will be because we need to set the base url for the site in our config.toml file.

Modify the baseurl in your config.toml file to point to your Netlify url.

```yaml
baseurl = "https://your-site-name.netlify.com/"`
```

Now push your site to GitHub again and your styles should be pulling through correctly.

You'll notice that just pushing to your master branch is enough to deploy a new change to your site.

Enjoy your new Hugo blog hosted on Netlify!

[hugo-new-site]: /images/hugo-new-site.png "hugo new site output"
[netlify-create-a-new-site]: /images/netlify-create-a-new-site.png "netlify create a new site"
[netlify-deploy-settings]: /images/netlify-deploy-settings.png "netlify deploy settings"
[netlify-advanced-build-settings]: /images/netlify-advanced-build-settings.png "netlify advanced build settings"
