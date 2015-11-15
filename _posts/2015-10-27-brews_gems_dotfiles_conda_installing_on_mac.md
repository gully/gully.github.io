---
layout:     post
title:      Installing on Mac with Brew, Dotfiles, Conda
date:       2015-11-15 05:00:00
summary:    There are tons of awesome software packages, modules, scripts, repositories, and apps out there.  This blog post is about the software and strategies for configuration management on one's personal computer, as told from my recent experience installing software on a new laptop.  Is there a "right way" to install software?
---

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">For now I&#39;ll make an analog version of a Dockerfile for a new MacBook setup-- a blog post.</p>&mdash; gully_ (@gully_) <a href="https://twitter.com/gully_/status/654500856109252609">October 15, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## Preamble

There are tons of awesome software packages, modules, scripts, repositories, and apps out there.  They take all different shapes and sizes.  Their goal is to make our lives easier, if only we can install them and their dependencies.  [Dependency hell](https://en.wikipedia.org/wiki/Dependency_hell) has been written about in [other blog posts](http://www.pgbovine.net/command-line-bullshittery.htm) so I won't dwell on it here.  But suffice it to say that getting software to run is often a problem, especially within the academic community.  This blog post is about the software and strategies for tackling dependency hell, and more broadly [configuration management](https://en.wikipedia.org/wiki/Configuration_management), as told from my recent experience installing software on my new Macbook Pro.  

Over the last few years, several products have emerged that basically install software that installs software.  Some are:

- [Homebrew](http://brew.sh/)
- [conda](http://conda.pydata.org/docs/)
- [RVM](https://rvm.io/)
- [gem](https://rubygems.org/)
- [git](https://en.wikipedia.org/wiki/Git_(software))
- [Docker](https://www.docker.com/)
- [Puppet](https://puppetlabs.com/)
- [Vagrant](https://www.vagrantup.com/)
- [dotfiles](https://dotfiles.github.io/)
- App Store
- Bodega

These disparate tools have vastly different functions, and are probably better described as environment managers, package managers, configration managers, or version control systems.  But the common thread is that there is some code that is not working on your laptop, and you want to get it working on your laptop.

The software that installs software are divided into [the two cultures of computing](http://www.pgbovine.net/two-cultures-of-computing.htm): apps and commandline.  I will focus on commandline solutions.  Many of the commandline solutions have a format: `thing install package` where `thing` is the software that installs software, and `package` is the software.  There are also `Thingfile` solutions where one can make a file listing a bunch of packages, and the packages are all installed en masse with a command like `run Thingfile`.

I started my installation quest by looking for an omnibus `Thingfile` environment manager like Docker or Puppet.  That's when I stumbled upon [Boxen](https://github.com/boxen/our-boxen), which uses Puppet "under the hood".  Boxen installs specific versions of programs, and is therefore more convenient for teams, and less convenient for single users, who generally want the most recent stable version.  Boxen was either a neat opportunity to learn Puppet, or yet-another-distracting-devOps solution that was going to take more time than it was worth.  I moved on.

## Setting up a new Mac

I decided to stick with a mix of Homebrew and dotfiles to install my software.  I forked Mathias Behrens' dotfiles repo on GitHub.  The repo has many virtues, but by-far my favorite feature is the nice looking iTerm2 profile that is so vastly superior to the default black and white Terminal.app as to make the default virtually unusable now.

I attempted to `git clone` my dotfiles repo, but git on OS X requires XCode CommandLine Interface (CLI).  XCode CLI had been problematic for my old laptop, since XCode often caused conflicts with `gcc` versions on my laptop.  I found [this convenient guide](https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/Xcode.md) which tabulates which version of gcc each version of XCode uses.  That's nice.  Nevertheless, I installed XCode CLI, and was able to git clone.

I merged upstream changes in the dotfiles, encountered merge conflicts, so I installed Sublime Text 2.  One of my common workflows is a split screen with iTerm2 on one half, and Sublime Text 2 on the other half.  This screen division is simple with [Spectacle](https://www.spectacleapp.com/).

With the newly installed Sublime Text 2, I went through all the .osx files in the dotfiles repo.  There are so many customizations one can make.  Among the most important changes is "set a blazing fast cursor refresh rate", since it felt like minutes passed to scroll in the terminal otherwise.

I updated OS X in the App Store, for security reasons.  I set up my git global identity.  I ran the bootstrap.sh script in the dotfiles repo.  This did not require homebrew to be installed yet.  The default aliases in the `.aliases` file assume you have Dropbox, sublime text, Xcode, and some other things that I don't have and should probably remove, but I didn't bother.

I deleted a bunch of the default dock icons that I never use.  Mail, Contacts, Launchpad, Pages, Reminders.  Get rid of it all.

Next up was Homebrew.  I settled on making a Brewfile and using `cask`, which installs binaries for many familiar apps.  My attempt to edit the brewfile revealed that different Brewfile formats have existed over the last few years because the brew bundle project was apparently deprecated and then reinstated?  Confusing.  There are so many casks (like Skype, Slack, Google Chrome... you name it!).  An experiment with this on Skype shows that the apps do not find their way into the `/Applications` directory which really screws with the way most users interact with OS X.

The key idea was that I had to add this flag to my `.bash_profile`:
`export HOMEBREW_CASK_OPTS="--appdir=/Applications"`
Because otherwise the default is to `~/Applications`, which stinks!  To find out if your favorite app is a brew cask, just do:
`brew cask search`.

A sample from my brewfile is below, but my entire brewfile is available on GitHub in my `dotfiles` fork.  

```bash

## Casks

tap 'caskroom/cask'
cask 'skim'
cask 'slack'
cask 'skype'
cask 'spotify'
cask 'saoimage-ds9'
cask 'whatroute'
cask 'flash'
cask 'google-drive'
cask 'sourcetree'
cask 'xquartz'
cask 'inkscape'
cask 'thunderbird'

## Interesting casks worth trying someday:
# volatility, noun-project, mongodb, sketch, transmission, focus, amazon-cloud-drive, tableau, rescuetime, readcube, openoffice, omnigraffle, vagrant, puppet, pycharm

brew 'coreutils'
brew 'moreutils'
brew 'findutils'

brew 'git'
brew 'gifsicle'

brew 'vim', args: ['--override-system-vi']
#brew 'homebrew/science/astrometry-net'
```
 
I installed Flash so that Speedtest.net would work.

I installed atMonitor.  The product is no longer supported, (Since 2011 or 2012).  But it is my favorite activity monitor because it is free and easily customizable.  All I want to see is the CPU usage and the RAM usage.  And maybe the internet usage.  atMonitor was flakey and I had to repeatedly open and close the app to get it to work.  (Update-- atMonitor has been working well for over 6 weeks).

I downloaded Papers2.  Papers has a cask on Homebrew, but unfortunately it is only the most recent version, Papers3, which requires an additional license purchase, which I don't care to do.  I have my Papers library connected to Google Drive, so that I can access my papers from any location.  It's using 9.0/15.0 GB on the Google Drive.

Last thing to install is anaconda.  I installed Python3.4.  
I did:

```bash
conda update conda
conda update anaconda
conda create --name legacy python=2 pandas astropy numpy scipy seaborn
conda install jupyter
conda install cython
conda install MKL 
```

The last line requires a free download of MKL optimizations for academics.  I prepended /anaconda/bin to my $PATH variable.

I started cloning repos to my machine.  Pip installed emcee.  I installed RVM.  *Thought*: should I have a `changelog.md` for my system?  Seems like a good idea.  Why not?  I installed `jekyll` with RVM.  I made a Gemfile in my dotfiles repo.

## Conclusions

The most useful part of the install was the Brewfile and dotfiles.  If I want to set up a fresh new computer again, I can just run the brewfile, and I'll automatically have all the same apps.  The dotfiles are also paramount to maintaining the same setup across multiple machines.  There are probably much better ways to uniformize environments completely with vagrant, docker, etc, but my approach is probably a good reproducible solution for most people.  I hope this helps guide others to making dotfiles for your setups.



