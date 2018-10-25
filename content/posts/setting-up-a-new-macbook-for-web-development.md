---
title: "Setting Up a New Macbook for Web Development"
date: 2018-10-12T13:38:51+13:00
draft: false
---

I've just started using a MacBook Pro as my main development machine at work. As this is the first time I've used a Mac for web development, I'm documenting all the settings, installs, tips and tricks on how to get up and running with an awesome development machine.

---

### Homebrew

Before you install anything, it's best to install all your apps through [Homebrew](https://brew.sh/) which is a package manager for macOS. This makes updating much easier.

To install run the following in your terminal:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

To update all your apps installed by Homebrew, run `brew update` followed by `brew upgrade`.

Now that we've got brew installed let's start installing apps.

---

### Terminal

First let's replace the default terminal.
[ITerm2](https://www.iterm2.com/) is probably the most widely used and most recommended. I've also heard good things about [Hyper](https://hyper.is/) but I've also heard it can be heavy on performance and it's still missing a few features. It's definitely one to look out for in the future though.

```bash
brew cask install iterm2
```

Now that we've got ITerm2 installed let's set it up.

- [Install Oh My Zsh](https://ohmyz.sh/)
- [Install zsh autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [Install zsh syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [Install Z](https://github.com/rupa/z)

Here is my current [.zshrc](https://github.com/tomosewe/dotfiles/blob/master/.zshrc) with aliases etc.

There is an enourmous amount of customising that you can do with ITerm2, here are a few links I've found useful.

- [Oh-My-Zsh! Made for CLI Lovers](https://hackernoon.com/oh-my-zsh-made-for-cli-lovers-bea538d42ec1)
- [Oh My Zsh Community](https://ohmyz.sh/community.html)
- [Become A Command-Line Power User With Oh My ZSH And Z](https://www.smashingmagazine.com/2015/07/become-command-line-power-user-oh-my-zsh-z/)
- [Syntax: The command line for web developers](https://syntax.fm/show/013/the-command-line-for-web-developers)
- [Command Line Power User by Wes Bos](https://commandlinepoweruser.com/)
- [Oh My Zsh Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)
- [Oh My Zsh Docs](https://github.com/robbyrussell/oh-my-zsh/)

#### Terminal Themes

I'm currently using Wes Bos' [Cobalt2 theme](https://github.com/wesbos/Cobalt2-iterm) which is great.

If you're keen to install it you'll need to do these 2 steps first.

- [Install PIP](http://powerline.readthedocs.io/en/master/installation/osx.html)
- [Install powerline fonts](https://github.com/powerline/fonts)

#### A few of my own tweaks that i prefer

- `Profile>text>cursor`: Set to `underline`
- I like to set up my view as 4 windows in a grid.
- To make sure it stays this way when you open it each time, you need to save it as the `Default` workspace by going to `Window>Save window arrangement` and saving it as `Default`. Then in preferences: `General>Startup`: In the dropdown select `Open Default Window Arrangement`.

---

### [Visual Studio Code](https://code.visualstudio.com/)

Easily the best text editor right now. Updates every month. Heaps of great extensions. I have another [blog post](https://blog.tomosewe.com) on how I've got it all set up.

```bash
brew cask install visual-studio-code
```

### [Git](https://git-scm.com/)

```bash
brew install git
```

Here is my current [.gitconfig](https://github.com/tomosewe/dotfiles/blob/master/.gitconfig) with aliases etc.

Some resources around setting up your own .gitconfig:

- [Git Basics: Git Aliases](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

### [Trash](https://github.com/sindresorhus/trash)

Use the trash command instead of `rm` to send things to the trash.

```bash
npm install --global trash-cli
```

### [Tree](https://www.npmjs.com/package/tree-cli)

Tree allows you to pretty print a directory in the console.

```bash
npm install -g tree-cli
```

[Use Wes Bos' tree function in your .zshrc](https://gist.github.com/wesbos/1432b08749e3cd2aea22fcea2628e2ed)

### [NodeJS](https://nodejs.org/en/)

```bash
brew install node
```

### [NVM (Node version manager)](https://github.com/creationix/nvm)

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```

After installing NVM, also run the following script.
The script clones the nvm repository to ~/.nvm and adds the source line to your profile (~/.bash_profile, ~/.zshrc, ~/.profile, or ~/.bashrc).

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

### [AWS Command Line Interface](https://aws.amazon.com/cli/)

```bash
brew install awscli
```

### [Docker](https://www.docker.com/)

- [How to install](https://pilsniak.com/how-to-install-docker-on-mac-os-using-brew/)

### [.Net](https://www.microsoft.com/net)

- [Install the .Net SDK](https://www.microsoft.com/net/learn/get-started-with-dotnet-tutorial)

- [Xcode](https://itunes.apple.com/app/xcode/id497799835) is required to install Visual Studio for Mac.
- [Visual Studio For Mac](https://visualstudio.microsoft.com/vs/mac/)

---

### Mac Utilities

#### [Alfred](https://www.alfredapp.com/)

Productivity app for hotkeys, keywords, text expanding and more.

#### [Parallels](https://www.parallels.com/)

Provided by work so I can run a Windows VM, we have a few .NET codebases that require maintenance.

#### [Caffeine](https://caffeine.en.softonic.com/mac)

Simple tool that prevents your Mac from going to sleep, good for long installs or presentations.

#### [Spectacle](https://www.spectacleapp.com/)

Allows you to use hotkeys to control windows. Similar to the built in functionality in Windows.

#### [f.lux](https://justgetflux.com/)

Makes the color of your computer's display adapt to the time of day, warm at night and like sunlight during the day.

#### [Rocket](http://rocket.wolves.fm/r/HyT6be9QX)

Add emojis just like in Slack.

#### [Kap](https://getkap.co/)

Create gifs from your screen.

```bash
brew cask install kap
```

#### [YouTube-Dl](https://rg3.github.io/youtube-dl/)

Download YouTube videos using the command line.

```bash
brew install youtube-dl
```

#### [Cheatsheet](https://mediaatelier.com/CheatSheet/)

Shows you the shortcuts available for the current app you're using just by holding down ⌘.

```bash
brew cask install cheatsheet
```

#### [Notion](https://www.notion.so/desktop)

Note taking app that I've just started using, kind of like Trello and Evernote combined.

```bash
brew cask install notion
```

#### [Boostnote](https://boostnote.io/)

Great markdown editor, I mostly use this for draft blog posts. Offline only.

#### [neofetch](https://github.com/dylanaraps/neofetch)

Command-line system information tool.

```bash
brew install neofetchcreenfetch
```

#### [Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/)

```bash
brew cask install firefox-developer-edition
```

#### [Hugo](https://gohugo.io/)

Static site generator. It's what this blog is using.

```bash
brew install hugo
```

#### [Git Kraken](https://www.gitkraken.com/)

git gui client.

```bash
brew cask install gitkraken
```

#### [Aerial](https://github.com/JohnCoates/Aerial)

Use the Apple tv screensaver on your mac.

```bash
brew cask install aerial
```

---

## General Mac Settings

##### Enable tabbing through dialog windows - [Source: Wes Bos](https://wesbos.com/osx-dialog-boxes-keyboard-tab/)

- In Keyboard > Shortcuts: Select _All controls_ under _Full Keyboard Access_.

##### Mission Control

- Untick `Automatically rearrange Spaces based on most recent use`. This prevents your workspaces from jumping around. This really annoyed me until I realised it was doing this.

##### Hot corners

- I've got this setup to show mission control on all my corners as most of the other options don't really do it anything for me. This also makes it easy to access mission control when I'm using an external mouse.

##### Keyboard

- Tick all the boxes here.
- Move _Key Repeat_ and _Delay Until Repeat_ all the way to the right.
- Touch Bar Show _F1, F2 etc. Keys_.
- Press Fn key to _Expand Control Strip_.

##### Mouse & Trackpad

- Tick all the things

##### Sound

- Tick _Show volume in menu bar_

##### Finder

- Open _Finder_, in the top bar go to _Finder>Preferences_.
- Under _General_, _New finder windows show: Home directory_.
- Under _Sidebar_, tick all folders you want to see by default.
- Under _Advanced_, tick _Show all filename extensions_.
- In the top bar go to _View_, and show all the things.

##### Show hidden files and folders:

```bash
defaults write com.apple.finder AppleShowAllFiles -bool true
killall Finder
```

To hide them again:

```bash
defaults write com.apple.finder AppleShowAllFiles -bool false
killall Finder
```

---

### Helpful links

- [GitHub - tomosewe/dotfiles: My MacOS dotfiles](https://github.com/tomosewe/dotfiles)

- [Matthew Palmer (@\_matthewpalmer) on Twitter](https://twitter.com/_matthewpalmer)

- [Syntax.fm](https://syntax.fm/)

- [Making the Touch Bar finally useful :: By abandoning crappy Apple guidelines :: vas3k's blog](http://vas3k.com/blog/touchbar/)

- [A Pro’s Guide to the Best Secret Mac Features — Matthew Palmer](https://matthewpalmer.net/blog/2018/04/14/ultimate-pro-guide-best-secret-mac-features/index.html)

- [Setting up a macbook for a windows developer - Darragh ORiordan](https://www.darraghoriordan.com/2018/03/25/macbook-setup-for-windows-developer/)

- [Uses | Wes Bos](https://wesbos.com/uses/)

- [GitHub - wesbos/dotfiles: Hey wes what settings do you use?](https://github.com/wesbos/dotfiles)

- [GitHub - atomantic/dotfiles: 🖥️ Automated Configuration, Preferences and Software Installation for macOS](https://github.com/atomantic/dotfiles)
