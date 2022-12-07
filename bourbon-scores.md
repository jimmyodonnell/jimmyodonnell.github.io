---
layout: post
category: blog
title: Bourbon Scores
excerpt:
modified: 2022-12-07
tags:
comments: false
---

This is a plot of the rating/score against price for around 400 bourbon whiskey reviews on [The Whiskey Jug](https://thewhiskeyjug.com). You can use the buttons in the bottom left of the plot to zoom, pan, and revert to the original extent. Note that once you click the magnifying glass and zoom in, you need to click the magnifying glass again to stop the zoom behavior when scrolling. Points are colored by how many whiskeys had the exact combination of price and score (the max was seven whiskeys at $50;87%).

{% include bourbon-scores-scatter.html %}

I used `template_type="simple"` when exporting the plot using `mpld3.save_html()`. Thanks to [John Miller](https://www.johnwmillr.com/interactive-plots-in-jekyll/)!
