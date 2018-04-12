---
layout:     post
title:      Interactive widget design with Bokeh
date:       2018-04-15 18:00:00
summary:    I lay out the design and development of lightkurve.interact(), a bokeh-based Jupyter widget for immediate, seamless visualization of Kepler/K2 data.
---

The core philosophy of designing `interact()` appears in its [original](https://github.com/KeplerGO/lightkurve/issues/91) and [revised](https://github.com/KeplerGO/lightkurve/issues/98) GitHub Issues:

>The successful design of this feature hinges upon the TPF image being displayed effortlessly and instantly. That is: latency is near-zero---much less than human reaction time--- and no typing or clicking-through is needed. We also demand interactivity: a user may wish to zoom in on a region of interest while maintaining the linked, high-performance display.

>These user experience objectives drove us to select a design that adopts the javascript framework bokeh. We investigated a matplotlib design, but we observed much higher latency, with less customization out-of-the-box.

I was able to quickly develop a working prototype by following the [bokeh gallery](https://bokeh.pydata.org/en/latest/docs/gallery.html) and [bokeh-notebooks](https://github.com/bokeh/bokeh-notebooks).  My first prototype demo'ed the supernova/transient KSN2015K, [recently discovered in K2 data](https://www.nature.com/articles/s41550-018-0423-2).  I show that the time-series images' center-of-mass positions shift as the transient gains luminosity, peaking after a mere 2.2 days.

<img src="https://user-images.githubusercontent.com/860227/38392505-8f8f9682-38dc-11e8-8cd4-7eae40b9270b.gif" alt="KSN2015K prototype">


Already this demo showed me that the prototype was not only *useable*, but also *useful*: we can witness astrophysical centroid changes registered to their position in the lightcurve.  My next step was to incorporate the feature directly into `lightkurve`, which I did in a [GitHub pull request](https://github.com/KeplerGO/lightkurve/pull/100).  I lengthened the slider bar, which gave more granular control over the lightcurve cadence position.  I also added a *play* functionality to automatically animate the slider bar:

<img src="https://user-images.githubusercontent.com/860227/38396349-5beedcec-38ec-11e8-93d9-736460c12e16.gif" alt="quicklook bokeh demo">

I renamed the tool from `quick_look()` to `interact()`, upon the guidance of K2 Guest Observer Office Director Geert Barentsen, and added a second slider for controlling the screen stretch.  The screen stretch is really helpful for finding faint objects right at the background noise limit.  In this example I identify an asteroid going through the upper right corner of the postage stamp.  


<img src="https://user-images.githubusercontent.com/860227/38585992-b96a1ab6-3cd0-11e8-9699-7c124ee69e33.gif" alt="Two slider demo">


I hit a snag when placing the screen stetch onto a log scale.  The bokeh colormapper
