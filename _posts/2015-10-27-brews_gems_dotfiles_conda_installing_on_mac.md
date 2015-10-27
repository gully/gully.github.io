---
layout:     post
title:      Brews, Gems, Dotfiles, Conda: Install on Mac
date:       2015-09-24 22:00:00
summary:    There are tons of awesome software packages, modules, scripts, repositories, and apps out there.  This blog post is about the software and strategies for configuration management on one's personal computer, as told from my recent experience installing software on a new laptop.  Is there a "right way" to install software?
---

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">For now I&#39;ll make an analog version of a Dockerfile for a new MacBook setup-- a blog post.</p>&mdash; gully_ (@gully_) <a href="https://twitter.com/gully_/status/654500856109252609">October 15, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## Preamble

There are tons of awesome software packages, modules, scripts, repositories, and apps out there.  They take all different shapes and sizes.  Their goal is to make our lives easier, if only we can install them and their dependencies.  [Dependency hell](https://en.wikipedia.org/wiki/Dependency_hell) has been written about in other blog posts and tweets, so I won't dwell on it here, but suffice it to say that getting software to run is often a problem, especially within the academic community.  This blog post is about the software and strategies for tackling dependency hell, and more broadly [configuration management](https://en.wikipedia.org/wiki/Configuration_management), as told from my recent experience installing software on my new Macbook Pro.  

Over the last few years, several products have emerged that basically install software that installs software.  Some are:

- Homebrew
- conda
- RVM
- gem
- git
- Docker
- Puppet
- Vagrant
- App Store
- dotfiles
- Bodega

These disparate tools have vastly different functions, and are probably better described as environment managers, package managers, configration managers, or version control systems.  But 18-wheelers, aluminum cans, and straws all get Mountain Dew to your mouth, and the common thread here is likewise: there is some code that is not working on your laptop, and you want to get it working on your laptop.

The software that installs software are divided into [the two cultures of computing](): apps and commandline.  I will focus on commandline solutions.  Many of the commandline solutions have a format: `thing install package` where `thing` is the software that installs software, and `package` is the software.  There are also `Thingfile` solutions where one can make a file listing a bunch of packages, and the packages are all installed en masse with a command like `run Thingfile`.

I started my installation quest by looking for an omnibus `Thingfile` environment manager like Docker or Puppet.  That's when I stumbled upon Boxen, which uses Puppet "under the hood".  Boxen installs specific versions of programs, and is therefore more convenient for teams, and less convenient for single users, who generally want the most recent stable version.  Boxen was either a neat opportunity to learn Puppet, or yet-another-distracting-devOps solution that was going to take more time than it was worth.  I moved on.

## Setting up a new Mac

I decided to stick with a mix of Homebrew and dotfiles to install my software.  Many astronomers agree that putting dotfiles under version control makes a lot of sense.  I forked Mathias Behrens' dotfiles repo on GitHub.  The repo has many virtues, but by-far my favorite feature is the nice looking iTerm2 profile that is so vastly superior to the default black and white Terminal.app as to make it virtually unusable.

I attempted to `git clone` my dotfiles repo, but git on OS X requires XCode CommandLine Interface (CLI).  XCode CLI had been problematic for my old laptop, since XCode often caused conflicts with `gcc` versions on my laptop.  I found this convenient guide which compiles which version of gcc each version of XCode uses.  That's nice.  Nevertheless, I installed XCode CLI, and was able to git clone.

I installed 1Password but could not sync my encrypted and synced files since Dropbox is blocked in China.

I merged upstream changes in the dotfiles, encountered merge conflicts, so I installed Sublime Text 2.  One of my common workflows is a split screen with iTerm2 on one half, and Sublime Text 2 on the other half.  This screen division is simple with Spectacle.  So I installed that.  

With the newly installed Sublime Text 2, I went through all the .osx files in the dotfiles repo.  There are so many customizations one can make.  Among the most important changes is "set a blazing fast cursor refresh rate", since it felt like minutes passed to scroll in the terminal otherwise.

I updated OS X in the App Store, for security reasons.  Next up was Homebrew.
 




