---
layout:     post
title:      The first UT Austin astronomy hack day
date:       2015-03-02 17:30:00
summary:    The UT Austin Astronomy Department graduate students and postdocs held their first hack day on Friday January 16, 2015.  We had 10 attendees and worked on 7 different projects.  This post summarizes the motivation, project outcomes, and lessons learned from our first experience.
categories: astronomy
---

The UT Austin Astronomy Department graduate students and postdocs held their first hack day on Friday January 16, 2015.  We had 10 attendees and worked on 7 different projects.  This post summarizes the motivation, project outcomes, and lessons learned from our first experience.

![photo of UT Austin Hack Day](/public/photos/UTAustin_Hack_day_photo.jpg)


#### Motivation and format

Stefano Meschiari and I came up with the idea to host an astronomy hack day at UT Austin.  Stefano and I had recently attended international astronomy hackathons in the last year- Stefano at [.Astronomy](http://dotastronomy.com/) and me at [SPIE](http://adsabs.harvard.edu/abs/2014SPIE.9152E..02K) and [Astro Data Hack Week](http://astrohackweek.github.io/).  We agreed that hackathons were really fun and productive.


A hack day consists of collaborative focused work effort, typically on a computer coding project.  Ideas are pitched at the beginning of the day. Self-assembled teams work together with limited time to achieve a common goal. At the end of the hack day the teams present their product.  Above all, a hack day is useful to learn from our colleagues, and maybe create something novel that could not have emerged without the confluence of skills unique to the people in the room.

#### Preparation

We picked a date after the winter AAS meeting but before classes had resumed for Spring semester.  This academic doldrums offered the fewest scheduling conflicts with classes and room reservation.  Still, several Department members expressed regret about having to miss the event.  All postdocs and graduate students were invited.  We did not include faculty in the email invitation, though not by design.  A few weeks before the hack day, I set up a GitHub wiki where Department members could identify themselves as participants, and view or add hack ideas.  Ultimately ten people added themselves to the [participants list](https://github.com/OttoStruve/UTAstroHackDay2015/wiki/Participants), and six people edited the [ideas list](https://github.com/OttoStruve/UTAstroHackDay2015/wiki/Hack-Ideas).

#### Hack Day 

Ten people showed up in the morning for the pitches.  After the pitches, the participants splintered into 5 groups of one to three people.


**Spectral continuum estimation** Kyle Kaplan and Yao-Lun Yang worked on automatic continuum estimation for spectral analysis.  Their applications differed, but their needs were similar.  Kyle needs to normalize IGRINS echelle orders, while Yao-Lun needs to fit Herschel data.  Kyle and Yao-Lun summarized their progress at the end of the day.

**Improving the IGRINS pipeline** Natalie Gosnell and Greg Mace worked on improvements to the IGRINS pipeline, including easy output of normalized IGRINS spectra to ASCII files to facilitate data sharing.

**Documentation for Systemic** Greg Mace used Stefano Meschiari's existing code, Systemic, to model orbital dynamics for radial velocity data.  Stefano aided Greg and improved the documentation in situ.

**Robust spectral inference for IGRINS data** Michael Gully-Santiago, Andy Mann, and Kevin Gullikson worked on implementing robust inference of IGRINS infrared stellar spectra with the new [Starfish code](http://iancze.github.io/Starfish/).  I wrote [a blog post](http://gully.github.io/2015/03/02/gully-starfish_hack/) about it in more detail.  Briefly, we worked on getting the code to work, and ultimately had a Skype call with the author of the code, Ian Czekala.  We also requested and got approval for 50,000 SU Startup allowance on the Wrangler Supercomputer at TACC.

**ADS developer API** Stefano Meschiari used the SAO/NASA Astrophysics Data System's "ADS developer API" to query ADS.  Stefano made an "Astronomy Publication Main Sequence" which plotted number of publications versus number of citations for individual authors on ADS.  The sequence revealed a characteristic trend, with some interesting outliers.  Stefano has expressed interest in posting his results online. 

**Interactive plots in browser** Ivan Ramierez used the [Bokeh Plotting Library](http://bokeh.pydata.org/) to make interactive in-browser visualizations.

Other attendees included Casey Deen (MPIA), who worked on his code [Moog Stokes](https://github.com/soylentdeen/MoogStokes/).

### Outcomes

At the end of the hack day we displayed our results and gathered to share feedback on the experience.  The feedback was positive- everyone enthusiastically agreed that we should host another hack day.  We had different recommendations for the frequency- Stefano and others suggested once per month.  Others highlighted the challenge of competing with classroom reservations, and teaching committments.  Other suggestions included more snacks and broader advertisement.  One participant confessed a reluctance to participate before the event, but was pleasantly surprised with how productive and collaborative the event turned out.  

We are currently planning another hack day over Spring Break (during SXSW in Austin).  We hope you will participate!

