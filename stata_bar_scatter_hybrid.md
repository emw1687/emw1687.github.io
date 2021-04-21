---
layout: post
title: Stata bar/scatter hybrid
author: CT
tags: stata bar scatter hybrid
---

![Stata bar/scatter hybrid](/images/stata_bar_scatter_hybrid.png)


```stata
/* data setup */
set seed 321
set obs 10
gen dst_id = _n

expand 10
gen sch_z = cond(mod(_n,2)==1, rnormal(0, 1), rnormal(0.25, 0.5))

egen dst_z = mean(sch_z), by(dst_id)
egen dst_tag = tag(dst_id)

qui summ sch_z
local overall_z = r(mean)

/* plot */
local xlabs `"1 "A" 2 "B" 3 "C" 4 "D" 5 "E" 6 "F" 7 "G" 8 "H" 9 "I" 10 "J""'

graph twoway ///
  (bar dst_z dst_id, ///
    barwidth(0.75) color("241 181 28")), || ///
  (scatter sch_z dst_id, ///
    msymbol(circle) mcolor("4 107 92") msize(medsmall)) || ///
  (function y = `overall_z', ///
    range(0 11) lcolor("208 43 39") lpattern(shortdash)), ///
  yline(0, lcolor(black) lwidth(vthin)) ///
  ylabel(-2(1)2, labsize(medsmall)) ///
  yscale(range(-2 2)) ///
  ytitle("Impact (z-score units)", size(medsmall)) yscale(titlegap(*3)) ///
  xlabel(`xlabs', labsize(medsmall)) ///
  xtitle("District", size(medsmall)) xscale(titlegap(*3)) ///
  xscale(range(0 10)) ///
  legend(order(3 "Overall impact" 1 "District impact" 2 "School impact") rows(1)) ///
  scheme(s1mono) graphregion(style(none)) plotregion(style(none))
```
