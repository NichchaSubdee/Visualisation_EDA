Visualisation and EDA
================

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   4.0.0     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(patchwork)
library(p8105.datasets)
```

``` r
data("weather_df")
```

Let’s make out basic catterplot

``` r
weather_df |>
     ggplot(aes(x = tmin, y = tmax)) + 
     geom_point(aes(color = name), alpha = 0.5) +
     labs(
       x = "Minimum daily temp",
       y = "Maximum daily temp",
       title = "Temperature scatterplot",
       caption = "Data from NOAA"
     )
```

    ## Warning: Removed 17 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Visualisation_EDA_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->
