
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Sumcolumnmiss

The goal of the sumcolumnmiss package is to count missing values for all
columns by group

## Installation

You can install the development version of GroupCount from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("stat545ubc-2023/sumcolumnmiss", quiet = TRUE)
```

## Examples

This illustration calculates the count of missing values in the
airquality dataset, organized by the “cyl” column.

``` r
library(sumcolumnmiss)
count_all_missing_by_group(airquality, Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

This instance produces identical results to the previous one,
highlighting an alternative approach to calling the
count_all_missing_by_group(): by piping the dataset directly into the
function.

``` r
airquality |> count_all_missing_by_group(Month) 
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

The “.groups” parameter, when specified, enables us to maintain the
grouped structure of the output based on the grouping column. In the
example below, observe the grouped tibble output, which contrasts with
the ungrouped tibble results from the earlier examples.

``` r
count_all_missing_by_group(airquality, Month, .groups = "keep")
#> # A tibble: 5 × 6
#> # Groups:   Month [5]
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```
