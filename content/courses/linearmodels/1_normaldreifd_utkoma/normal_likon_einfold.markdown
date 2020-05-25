---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: Ein skýribreyta
menu:
  linearmodels:
    parent: "1. Normaldreifð útkoma"
    weight: 1
title: Ein skýribreyta
toc: true
type: docs
weight: 1
---


```r
library(broom)
m <- lm(mpg ~ wt, data = mtcars)
tidy(m)
```

```
## # A tibble: 2 x 5
##   term        estimate std.error statistic  p.value
##   <chr>          <dbl>     <dbl>     <dbl>    <dbl>
## 1 (Intercept)    37.3      1.88      19.9  8.24e-19
## 2 wt             -5.34     0.559     -9.56 1.29e-10
```


```r
library(emmeans)
emmeans(m, ~ wt, at = list(wt = seq(from = 1, to = 4, length.out = 20)))
```

```
##    wt emmean    SE df lower.CL upper.CL
##  1.00   31.9 1.352 30     29.2     34.7
##  1.16   31.1 1.271 30     28.5     33.7
##  1.32   30.3 1.192 30     27.8     32.7
##  1.47   29.4 1.114 30     27.1     31.7
##  1.63   28.6 1.037 30     26.4     30.7
##  1.79   27.7 0.963 30     25.8     29.7
##  1.95   26.9 0.891 30     25.1     28.7
##  2.11   26.0 0.822 30     24.4     27.7
##  2.26   25.2 0.758 30     23.6     26.7
##  2.42   24.3 0.699 30     22.9     25.8
##  2.58   23.5 0.646 30     22.2     24.8
##  2.74   22.7 0.602 30     21.4     23.9
##  2.89   21.8 0.568 30     20.7     23.0
##  3.05   21.0 0.546 30     19.9     22.1
##  3.21   20.1 0.538 30     19.0     21.2
##  3.37   19.3 0.545 30     18.2     20.4
##  3.53   18.4 0.565 30     17.3     19.6
##  3.68   17.6 0.598 30     16.4     18.8
##  3.84   16.8 0.642 30     15.4     18.1
##  4.00   15.9 0.694 30     14.5     17.3
## 
## Confidence level used: 0.95
```

