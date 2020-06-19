---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: "Ein skýribreyta  "
menu:
  linearmodels:
    parent: Talningar útkoma
    weight: 3
title: "Ein skýribreyta  "
toc: true
type: docs
weight: 3 * 10 + 1
---


```r
library(broom)
library(faraway)
m <- glm(Species ~ Elevation, data = gala, family = poisson)
tidy(m)
```

```
## # A tibble: 2 x 5
##   term        estimate std.error statistic p.value
##   <chr>          <dbl>     <dbl>     <dbl>   <dbl>
## 1 (Intercept)  3.66    0.0316        116.        0
## 2 Elevation    0.00144 0.0000318      45.1       0
```


```r
library(emmeans)
emmeans(m, ~ Elevation, at = list(Elevation = c(90, 300)), type = "response")
```

```
##  Elevation rate   SE  df asymp.LCL asymp.UCL
##         90 44.4 1.31 Inf      41.9      47.1
##        300 60.1 1.49 Inf      57.2      63.1
## 
## Confidence level used: 0.95 
## Intervals are back-transformed from the log scale
```

