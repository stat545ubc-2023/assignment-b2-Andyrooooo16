
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Sumcolumnmiss

The goal of the sumcolumnmiss package is to count missing values for all
columns by group

## Installation

You can install the development version of GroupCount from
[GitHub](https://github.com/) with:

``` r

# install.packages("devtools")
devtools::install_github("stat545ubc-2023/sumcolumnmiss")
#> Downloading GitHub repo stat545ubc-2023/sumcolumnmiss@HEAD
#> Installing 6 packages: vctrs, rlang, xfun, utf8, fansi, htmltools
#> Installing packages into 'C:/Users/andre/AppData/Local/R/win-library/4.3'
#> (as 'lib' is unspecified)
#> Warning: cannot remove prior installation of package 'vctrs'
#> Warning in file.copy(savedcopy, lib, recursive = TRUE): problem copying
#> C:\Users\andre\AppData\Local\R\win-library\4.3\00LOCK\vctrs\libs\x64\vctrs.dll
#> to C:\Users\andre\AppData\Local\R\win-library\4.3\vctrs\libs\x64\vctrs.dll:
#> Permission denied
#> Warning: restored 'vctrs'
#> Warning: cannot remove prior installation of package 'rlang'
#> Warning in file.copy(savedcopy, lib, recursive = TRUE): problem copying
#> C:\Users\andre\AppData\Local\R\win-library\4.3\00LOCK\rlang\libs\x64\rlang.dll
#> to C:\Users\andre\AppData\Local\R\win-library\4.3\rlang\libs\x64\rlang.dll:
#> Permission denied
#> Warning: restored 'rlang'
#> Warning: cannot remove prior installation of package 'xfun'
#> Warning in file.copy(savedcopy, lib, recursive = TRUE): problem copying
#> C:\Users\andre\AppData\Local\R\win-library\4.3\00LOCK\xfun\libs\x64\xfun.dll to
#> C:\Users\andre\AppData\Local\R\win-library\4.3\xfun\libs\x64\xfun.dll:
#> Permission denied
#> Warning: restored 'xfun'
#> Warning: cannot remove prior installation of package 'utf8'
#> Warning in file.copy(savedcopy, lib, recursive = TRUE): problem copying
#> C:\Users\andre\AppData\Local\R\win-library\4.3\00LOCK\utf8\libs\x64\utf8.dll to
#> C:\Users\andre\AppData\Local\R\win-library\4.3\utf8\libs\x64\utf8.dll:
#> Permission denied
#> Warning: restored 'utf8'
#> Warning: cannot remove prior installation of package 'fansi'
#> Warning in file.copy(savedcopy, lib, recursive = TRUE): problem copying
#> C:\Users\andre\AppData\Local\R\win-library\4.3\00LOCK\fansi\libs\x64\fansi.dll
#> to C:\Users\andre\AppData\Local\R\win-library\4.3\fansi\libs\x64\fansi.dll:
#> Permission denied
#> Warning: restored 'fansi'
#> Warning: cannot remove prior installation of package 'htmltools'
#> Warning in file.copy(savedcopy, lib, recursive = TRUE): problem copying
#> C:\Users\andre\AppData\Local\R\win-library\4.3\00LOCK\htmltools\libs\x64\htmltools.dll
#> to
#> C:\Users\andre\AppData\Local\R\win-library\4.3\htmltools\libs\x64\htmltools.dll:
#> Permission denied
#> Warning: restored 'htmltools'
#> Warning: package 'sumcolumnmiss' is in use and will not be installed
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
