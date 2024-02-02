week2
================
2024-01-31

- [Statistics on S&P returns](#statistics-on-sp-returns)
- [S&P Prices](#sp-prices)
- [S&P Yearly Returns](#sp-yearly-returns)

## Statistics on S&P returns

- The cumulative returns of the S&P index during this period is 2.18%.
- The average daily returns of the S&P index during this period is 0%.
- The standard deviation of the daily returns of the S&P index during
  this period is 0.01%.

## S&P Prices

``` r
library(ggplot2)

ggplot(data, aes(x = date, y = SPY_prices)) +
  geom_line()
```

![](week2_lecture_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

## S&P Yearly Returns

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(lubridate)
```

    ## 
    ## Attaching package: 'lubridate'

    ## The following objects are masked from 'package:base':
    ## 
    ##     date, intersect, setdiff, union

``` r
yearly = data %>% 
  mutate(year = year(date)) %>% 
  filter(year < 2024) %>% 
  group_by(year) %>% 
  summarise(yearly_returns = sum(SPY_returns)*100)

ggplot(yearly, aes(x=year, y=yearly_returns)) +
  geom_col()
```

![](week2_lecture_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->
