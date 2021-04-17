---
layout: post
title: Stata density plot
author: AD
tags: stata "density plot"
---

![Stata density plot](/images/stata_density_plot.png)


```stata
tw (histogram pctKept if female==0, width(5) color(none) lcolor(black) lpattern(dash)) ///        
       (histogram pctKept if female==1, width(5) color(navy%30)), ///   
       legend(rows(1) order(1 "Male respondent" 2 "Female respondent") region(col(white))) graphregion(color(white))  yla(, angle(0))  xtitle("Share of crop harvest kept for household consumption (%)")
```