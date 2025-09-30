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

## Scale

``` r
weather_df |>
     ggplot(aes(x = tmin, y = tmax)) + 
     geom_point(aes(color = name), alpha = 0.5) +
     labs(
       x = "Minimum daily temp",
       y = "Maximum daily temp",
       title = "Temperature scatterplot",
       caption = "Data from NOAA"
     ) +
  scale_x_continuous(
    breaks = c(-20, 0, 25),
    labels = c("-20C", "0", "25")
  ) +
  scale_y_continuous(
    trans = "sqrt",
    limits = c(10, 30)
  )
```

    ## Warning in transformation$transform(x): NaNs produced

    ## Warning in scale_y_continuous(trans = "sqrt", limits = c(10, 30)): sqrt
    ## transformation introduced infinite values.

    ## Warning: Removed 843 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Visualisation_EDA_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
weather_df |>
     filter(tmax > 10, tmax < 30) |> 
     ggplot(aes(x = tmin, y = tmax)) + 
     geom_point(aes(color = name), alpha = 0.5) +
     labs(
       x = "Minimum daily temp",
       y = "Maximum daily temp",
       title = "Temperature scatterplot",
       caption = "Data from NOAA"
     ) +
  scale_x_continuous(
    breaks = c(-20, 0, 25),
    labels = c("-20C", "0", "25")
  ) +
  scale_y_continuous(
    trans = "sqrt",
    limits = c(10, 30)
  )
```

![](Visualisation_EDA_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
weather_df |>
     filter(tmax > 10, tmax < 30) |> 
     ggplot(aes(x = tmin, y = tmax)) + 
     geom_point(aes(color = name), alpha = 0.5) +
     labs(
       x = "Minimum daily temp",
       y = "Maximum daily temp",
       title = "Temperature scatterplot",
       caption = "Data from NOAA"
     ) +
  scale_x_continuous(
    breaks = c(-20, 0, 25),
    labels = c("-20C", "0", "25")
  ) +
  scale_color_hue(h = c(100, 300))
```

![](Visualisation_EDA_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
# change color like this is not good idea to do, do viridis package
```

``` r
library(viridis)
```

    ## Loading required package: viridisLite

``` r
ggp_temp_plot = 
  weather_df |> 
  ggplot(aes(x = tmin, y = tmax)) + 
  geom_point(aes(color = name), alpha = .5) + 
  labs(
    title = "Temperature plot",
    x = "Minimum daily temperature (C)",
    y = "Maxiumum daily temperature (C)",
    color = "Location",
    caption = "Data from the rnoaa package"
  ) + 
  viridis::scale_color_viridis(
    name = "Location", 
    discrete = TRUE
  )
ggp_temp_plot
```

    ## Warning: Removed 17 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Visualisation_EDA_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->
