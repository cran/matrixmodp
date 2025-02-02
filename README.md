
<!-- README.md is generated from README.Rmd. Please edit that file -->

# matrixmodp

<!-- badges: start -->

[![R-CMD-check](https://github.com/rhigginbottom/matrixmodp/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/rhigginbottom/matrixmodp/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

The goal of matrixmodp is to make two matrix algebra tasks easier when
working with the fields $\mathbb{F}_p$. Specifically, this package
provides two functions: `rref_p()` calculates the reduced-row echelon
form of a matrix, and `inv_p()` calculates the inverse of a (square,
invertible) matrix.

## Installation

You can install the public released version of `matrixmodp` from CRAN
with:

``` r
install.packages("matrixmodp")
#> Installing package into 'C:/Users/rhigginbottom/AppData/Local/Temp/Rtmpc35hmI/temp_libpath93c0442736d5'
#> (as 'lib' is unspecified)
#> Warning: package 'matrixmodp' is not available for this version of R
#> 
#> A version of this package for your version of R might be available elsewhere,
#> see the ideas at
#> https://cran.r-project.org/doc/manuals/r-patched/R-admin.html#Installing-packages
```

You can install the development version of matrixmodp from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("rhigginbottom/matrixmodp")
```

## Example

We first provide an example of finding the RREF of a matrix with entries
in $\mathbb{F}_5$.

``` r
library(matrixmodp)
entries <- c(4, 1, 2, 0, 0, 3, 4, 0, 0, 1, 4, 1)
A <- matrix(entries, 3, 4)
rref_p(A, 5)
#>      [,1] [,2] [,3] [,4]
#> [1,]    1    0    0    4
#> [2,]    0    1    0    1
#> [3,]    0    0    1    0
```

We now show how to find the inverse of a $3\times 3$ matrix over
$\mathbb{F}_7$.

``` r
library(matrixmodp)
entries <- c(3, 3, 3, 2, 0, 2, 1, 2, 5)
A <- matrix(entries, 3, 3)
inv_p(A, 7)
#>      [,1] [,2] [,3]
#> [1,]    6    5    1
#> [2,]    3    3    1
#> [3,]    5    0    2
```

## Note

Some of the code for the `rref_p()` function was taken from the
`echelon()` function in the `matlib` package. Because of the different
way row operations need to work when using entries in $\mathbb{F}_p$, no
functions could be copied entirely. This makes attribution somewhat
difficult. The license chosen for this package was specifically chosen
to be compatible with the license in use for the `matlib` package
because of this overlap in code.
