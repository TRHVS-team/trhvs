---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: "Fleiri skýribreytur  "
menu:
  linearmodels:
    parent: Talningar útkoma
    weight: 3
title: "Fleiri skýribreytur  "
toc: true
type: docs
weight: 3 * 10 + 2
---


```r
library(broom)
library(faraway)
m <- glm(Species ~ Elevation + Area, data = gala, family = poisson)
tidy(m)
```

```
## # A tibble: 3 x 5
##   term          estimate std.error statistic   p.value
##   <chr>            <dbl>     <dbl>     <dbl>     <dbl>
## 1 (Intercept)  3.62      0.0339       107.   0.       
## 2 Elevation    0.00158   0.0000498     31.7  7.04e-220
## 3 Area        -0.0000662 0.0000186     -3.55 3.81e-  4
```


```r
library(emmeans)
emmeans(m, ~ Elevation + Area, at = list(Elevation = c(90, 300),
                                         Area = c(2, 50)), type = "response")
```

```
##  Elevation Area rate   SE  df asymp.LCL asymp.UCL
##         90    2 43.1 1.33 Inf      40.6      45.8
##        300    2 60.1 1.50 Inf      57.2      63.1
##         90   50 43.0 1.33 Inf      40.5      45.7
##        300   50 59.9 1.50 Inf      57.0      62.9
## 
## Confidence level used: 0.95 
## Intervals are back-transformed from the log scale
```

