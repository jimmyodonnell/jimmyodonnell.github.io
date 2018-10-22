---
layout: post
category: blog
title: Haplotype networks in R updated
excerpt: 
date: 2013-11-23
tags: [R, DNA]
comments: false
---
I’ve gotten a good deal of feedback about the haplotype network script I posted (apparently nobody cares about pad thai around here!). A colleague was having trouble getting names to match up in her sites file and alignment. After reviewing the script, I noticed the cause of the problem: my self-taught hack programming skills. Perhaps something changed since I wrote it, but more likely, there was something specific about the sample and site names of the data I was working with that caused the script to work at that time. In any case, I’ve fixed it now, and uploaded working example files. I remain too lazy to match up names using the function match(), but will probably get around to that at some point. You can get the goods over at the resources page or [here](https://drive.google.com/folderview?id=0ByS-qEQSbq9dZ1laaHdtSmhiYmM&usp=sharing).

The offending line:

`identical(levels(sites$sample),labels(alignment))`

Should instead read:

`identical(as.character(sites$sample),labels(alignment))`
