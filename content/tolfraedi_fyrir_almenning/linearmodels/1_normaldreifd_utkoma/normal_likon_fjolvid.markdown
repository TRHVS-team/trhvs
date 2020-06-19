---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: Fleiri skýribreytur
menu:
  linearmodels:
    parent: Normaldreifð útkoma
    weight: 2
title: Fleiri skýribreytur
toc: true
type: docs
weight: 2
---


```r
library(broom)
m <- lm(mpg ~ wt + hp, data = mtcars)
tidy(m)
```

```
## # A tibble: 3 x 5
##   term        estimate std.error statistic  p.value
##   <chr>          <dbl>     <dbl>     <dbl>    <dbl>
## 1 (Intercept)  37.2      1.60        23.3  2.57e-20
## 2 wt           -3.88     0.633       -6.13 1.12e- 6
## 3 hp           -0.0318   0.00903     -3.52 1.45e- 3
```


```r
library(emmeans)
emmeans(m, ~ wt + hp, 
        at = list(wt = c(2, 3),
                  hp = c(90, 110)))
```

```
##  wt  hp emmean    SE df lower.CL upper.CL
##   2  90   26.6 0.739 29     25.1     28.1
##   3  90   22.7 0.631 29     21.4     24.0
##   2 110   26.0 0.760 29     24.4     27.5
##   3 110   22.1 0.528 29     21.0     23.2
## 
## Confidence level used: 0.95
```
