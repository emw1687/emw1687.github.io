---
layout: post
title: Stata bar chart
author: AD
tags: stata "bar chart"
---

![Stata bar chart](/images/stata_bar_chart.png)


```stata
gr hbar h9q03a__, over(provider, sort(ct)) ///
       graphregion(color(white)) ///
       yla(, angle(0)) ///
       ytitle("Share of households receiving extension services" "advice/information (%)")
```