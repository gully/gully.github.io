---
layout:     post
title:      Interactive widgets for understanding K2 lightcurves
date:       2018-04-17 18:00:00
summary:    Distinguishing instrumental artifacts from bona fide astrophysical signals complicates the analysis of Kepler/K2 lightcurves, and any imperfectly acquired time series data for that matter.  In this blog post I narrate the design and implementation of a new interactive quick look tool for gauging whether the blip you see in your Kepler lightcurve could arise from something scientifically interesting or mere spacecraft noise.  The simple framework, code, and design choices can be adapted to a broad swath of modern astronomical datasets.
---

One of the most common questions we get at the Kepler/K2 Guest Observer Office is "I see a noise blip in my K2 lightcurve.  Is it real or instrumental?"  Answering the question usually entails ticking through our (long, incomplete) mental list of conceivable, sometimes exotic instrumental artifacts.  Space-craft induced periodic motion.  Rolling band.  Cosmic Rays.  Collateral cosmic rays.  Smear.  Sudden pixel sensitivity dropouts.  Fine-guidance-sensor cross talk.  Regular cross talk. [Sweater fuzzy](https://twitter.com/gully_/status/941707161058586624).

Sometimes the ephemeral signals arise from exotic astrophysics, but not the kind that interests our *K2-user-in-need*.  Asteroid conjunctions, Mars' bleed trail, background eclipsing binaries, and crowded fields all conspire to induce seemingly-real astrophysical signals.  **Many effects matter at the exceptional precision level of Kepler and K2.**

No single algorithm can distinguish the wheat from the chaff in Kepler lightcurves, though heuristics exist.  [K2Flix](https://github.com/KeplerGO/k2flix) provides user-friendly animated gifs that satisfy the inner Feynman- "You just look at the thing!".  The sane defaults for screen stretch mean that flares and rolling-band alike appear conspicuously in the [tweet-ready gifs](https://twitter.com/keplerbot?lang=en).

One missing ingredient evades K2Flix. Registering the fateful, flawed moment to the position in a lightcurve requires manual intervention by spot-checking a lookup-table of time, or cadence, or some other bespoke tool to snip out the irrecoverable data.  *I want to see the effect of the artifact on the lightcurve in real time.*  K2 Guest Observer Director Geert Barentsen has, for a long time, sought a tool that shows the K2 lightcurve with a slider bar that continually updates the TPF snapshot registered at the user-selected cadence.  

In this blog post I introduce such a quick-look tool, `interact()`, which will reside in the new general-purpose [lightkurve](http://lightkurve.keplerscience.org/) framework for astronomical time series data analysis.  I walk through the design and development of `interact()` in another blog post.  Here we show its final, salient features, for public consumption.

### `interact()`

The figure below...
