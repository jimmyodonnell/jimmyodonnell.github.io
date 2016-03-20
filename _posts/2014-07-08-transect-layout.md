---
layout: post
title: Transect Layout in R
date:   2014-07-08
excerpt: 
modified: 2011-08-11
tags: [R, spatial, ecology]
comments: false
---
I’m working with an awesome group of folks at NOAA’s [Northwest Fisheries Science Center](http://www.nwfsc.noaa.gov/) on a project investigating biodiversity of eelgrass habitats around Puget Sound, and our team (the [Kelly Lab](http://kellyresearchlab.com/)) is assessing the feasibility of [environmental DNA](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0086175) methods for this type of study. If we’re to be confident in our ability to detect differences among sites, we first need to know how far DNA molecules (and tissue fragments containing them) travel before degrading in these tidally influenced habitats.

To do this, I needed to set up some transects running away from a known DNA source along which we could collect water samples from a boat. I knew (1) where I wanted to start each transect, (2) what direction I wanted the transects to run, and (3) what distances along the transects I wanted to sample. I needed to get coordinates for sampling point along the transects–nothing too complicated, just some simple “SOH-CAH-TOA” with the twist of sampling on a round surface (the earth). As is often the case, I wrote some really sloppy code myself before stumbling on exactly the function I needed: [destPoint](http://www.inside-r.org/packages/cran/geosphere/docs/destPoint) in the very useful R package [geosphere](https://cran.r-project.org/web/packages/geosphere/index.html). It’s incredibly simple, and you can find some code demonstrating its usage over [here](https://gist.github.com/jimmyodonnell/f702fb7f229fdf529728) on my GitHub page.

![transects](/images/transects.png)
