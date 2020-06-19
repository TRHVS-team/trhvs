---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: "Ein skýribreyta "
menu:
  linearmodels:
    parent: Tvíkosta útkoma
    weight: 2
title: "Ein skýribreyta "
toc: true
type: docs
weight: 2 * 10 + 1
---


```r
library(tidyverse)
```

```
## ── Attaching packages ────────────────────────────────────────────────── tidyverse 1.3.0 ──
```

```
## ✓ ggplot2 3.3.1     ✓ purrr   0.3.4
## ✓ tibble  3.0.1     ✓ dplyr   1.0.0
## ✓ tidyr   1.1.0     ✓ stringr 1.4.0
## ✓ readr   1.3.1     ✓ forcats 0.5.0
```

```
## ── Conflicts ───────────────────────────────────────────────────── tidyverse_conflicts() ──
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(broom)
m <- glm(am ~ wt, data = mtcars, family = binomial)
tidy(m)
```

```
## # A tibble: 2 x 5
##   term        estimate std.error statistic p.value
##   <chr>          <dbl>     <dbl>     <dbl>   <dbl>
## 1 (Intercept)    12.0       4.51      2.67 0.00759
## 2 wt             -4.02      1.44     -2.80 0.00509
```


```r
library(emmeans)
emmeans(m, ~ wt, at = list(wt = c(1, 3)), type = "response")
```

```
##  wt   prob       SE  df asymp.LCL asymp.UCL
##   1 0.9997 0.001019 Inf    0.8763    1.0000
##   3 0.4921 0.151311 Inf    0.2283    0.7604
## 
## Confidence level used: 0.95 
## Intervals are back-transformed from the logit scale
```

