---
layout:     post
title:      How do astronomers discover resources?
date:       2015-11-25 05:00:00
summary:    Information sharing within the astronomy community occurs through many avenues.  In this blog post I point out that the current information sharing avenues are lacking an outlet for user contributed, community-curated, open-access content about astronomy specific resources.  I provide an implementation of this forum, called Awesome Astronomy, which is inspired by the Awesome lists on GitHub.
---

Information sharing within the astronomy community occurs through many avenues.  In this blog post I point out that the current information sharing avenues are lacking an outlet for user contributed, community-curated, open-access content about astronomy specific resources.  I provide an implementation of this forum, called [Awesome Astronomy](https://github.com/jonathansick/awesome-astronomy).

### Limitations of information sharing in astronomy

Beyond journals like [ApJ](http://iopscience.iop.org/0004-637X/) and preprint servers like [astroPH](http://arxiv.org/list/astro-ph/new), there are other less formal venues for discovering resources and exchanging ideas.  There is the (infamous?) [Astronomer's Facebook Group](https://www.facebook.com/groups/123898011017097/).  At least [190 astronomy tweeps](http://truesciphi.org/ast.html) have >1000 followers on Twitter.  [AstroBetter](http://www.astrobetter.com) is probably the premier destination for information sharing for professional astronomers, with searchable, curated, high quality content.  The nascent but active [astronomers.io](http://www.astronomers.io) provides an alternative format to the major social media platforms.  There are also probably dozens or hundreds of personal blogs.  My favorite is the [Hogg Blog](http://hoggresearch.blogspot.com).

From a user perspective, there is a problem that the ephemeral posts of social media formats limit their usefulness for discovering high quality content.  In other words, interesting Facebook posts from today will be buried below hundreds or thousands of other posts by a few months from now.  Members could, in principle, search archives of thousands of posts to find information on a specific topic.  But sorting the wheat from the chaff is still a barrier for the discovery of high quality content.

For example, yesterday my friend and former colleague Colette Salyk (Vassar) [posted an inquiry to the Astronomer's Facebook group](https://www.facebook.com/groups/123898011017097/permalink/958829230857300/), paraphrased here as:
> "Hi everyone, I'm looking to put together a set of "curated" astronomy datasets for use in 200-level astronomy and planetary science courses. Things like: sets of photometry for making HR diagrams, light curves of variable stars, stellar occultation light curves, radial velocity curves, etc. If you all have favorite (non-proprietary) datasets for this purpose could you point me to links and/or send me said data directly? I would likely eventually put these in a central location on the web for all to use."

A few other astronomers and I responded, highlighting resources like the [AstroML datasets](http://www.astroml.org/user_guide/datasets.html), SDSS, NASA, and my own ApJDataFrames repository.  But consider someone joining the Facebook group in several months or years.  This new member would probably not benefit from the valuable exchange that occurred between Colette, me, and the other astronomers.

From an open access perspective, all of these astronomy-specific social media groups are *closed*.  In other words, there is a gate keeper to prevent amateur astronomers or crackpots from contributing content that dillutes the focus of the group, which is professional astronomy.  But why should an interested amateur or and undergraduate student be denied access to the exchange that Colette and I had?  Not to mention the fact that in some countries, like the one I currently live in, Facebook and Twitter are *blocked*.  Yes, really.  No matter your feelings on blocked websites and the politics surrounding that, by relying on these blocked websites, you are ultimately denying astronomers in certain countries access to your content.

### Introducing the [Awesome Astronomy](https://github.com/jonathansick/awesome-astronomy) list

These problems have convinced me that there is room for yet-another-format for astronomy content discovery.  I propose that we leverage the simple design of the [Awesome List](https://github.com/sindresorhus/awesome) phenomenon: a user editable markdown file, that accepts pull requests from *anyone*.  The content of the markdown file is simply links to useful resources specific to the domain.  For example, there is already [Awesome Python](https://github.com/vinta/awesome-python) and [Awesome Public Datasets](https://github.com/caesar0301/awesome-public-datasets).  So an `Awesome Astronomy` list is simply a list of links to useful resources for astronomy.

There are further benefits of an Awesome Astronomy list.  Since it's just a markdown file that anyone can edit, the Awesome Astronomy list is the perfect first "pull request" for an astronomer new to `git` and GitHub.  It's generally [hard to gain experience with pull requests](https://medium.com/@kentcdodds/first-timers-only-78281ea47455#.rat2059p1), so this gentle introduction could serve as many peoples' first time.  In fact, [we tried the Awesome Astronomy experiment at the UT Austin Astronomy Department last year](https://github.com/OttoStruve/awesome-astronomy-tools), and it was a huge success!  Many students and postdocs made their first "open source" contribution using git and GitHub during a live demo.  And the content reflected the diversity of the participants.

The Awesome Astronomy list shares some similarities to the existing [AstroBetter wiki](http://www.astrobetter.com/wiki/Wiki+Home).  The benefit of maintaining an Awesome Astronomy list on GitHub is twofold-- as mentioned above, it's an opportunity for newcomers to practice GitHub pull requests.  But also, the Pull Request format provides a forum for the open discussion of what can or should be included in the curated list, via the comments sections surrounding pull requests.  It provides a natural democratization for the community to moderate contributions.  It decentralizes the power away from single gatekeeper, and back to the community.

The format is already popular across many other fields, so an Awesome Astronomy list will serve as a gateway for folks from other disciplines to find out about, use, and maybe contribute to our astronomy resources.  Ideally, the content from the AstroBetter Wiki would eventually find its way into the Awesome List.  But that's up to the community to decide with your pull requests!

So here it is: [https://github.com/jonathansick/awesome-astronomy](https://github.com/jonathansick/awesome-astronomy).  We welcome your contributions!