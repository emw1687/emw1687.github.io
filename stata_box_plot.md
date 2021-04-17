---
layout: post
title: Stata box plot
author: AD
tags: stata "box plot"
---

![Stata box plot](/images/stata_box_plot.png)


```stata
gr hbox condPctSold if sumCond > 10 & female == 1 [pw = wgt], over(crop_order) graphregion(color(white)) ///
    ytitle("Share of crop harvest sold (%)")
```