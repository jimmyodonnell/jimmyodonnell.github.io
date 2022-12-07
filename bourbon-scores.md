---
layout: post
category: blog
title: Bourbon Scores
excerpt:
modified: 2022-12-07
tags:
comments: false
---

This is a plot of the rating/score against price for around 400 bourbon whiskey reviews on [The Whiskey Jug](https://thewhiskeyjug.com).

{% include bourbon-scores-scatter.html %}

I used `template_type="simple"` when exporting the plot using `mpld3.save_html()`. Thanks to [John Miller](https://www.johnwmillr.com/interactive-plots-in-jekyll/)!
