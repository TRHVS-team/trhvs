---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: "Fleiri skýribreytur "
menu:
  linearmodels:
    parent: Tvíkosta útkoma
    weight: 2
title: "Fleiri skýribreytur "
toc: true
type: docs
weight: 2 * 10 + 2
---


```r
library(broom)
m <- glm(am ~ wt + hp, data = mtcars, family = binomial)
tidy(m)
```

```
## # A tibble: 3 x 5
##   term        estimate std.error statistic p.value
##   <chr>          <dbl>     <dbl>     <dbl>   <dbl>
## 1 (Intercept)  18.9       7.44        2.53 0.0113 
## 2 wt           -8.08      3.07       -2.63 0.00843
## 3 hp            0.0363    0.0177      2.04 0.0409
```


```r
library(emmeans)
emmeans(m, ~ wt + hp, 
        at = list(wt = c(2, 3),
                  hp = c(90, 110)),
        type = "response")
```

```
##  wt  hp  prob      SE  df asymp.LCL asymp.UCL
##   2  90 0.997 0.00649 Inf   0.73029     1.000
##   3  90 0.107 0.13178 Inf   0.00798     0.641
##   2 110 0.999 0.00339 Inf   0.79245     1.000
##   3 110 0.198 0.17792 Inf   0.02690     0.689
## 
## Confidence level used: 0.95 
## Intervals are back-transformed from the logit scale
```
