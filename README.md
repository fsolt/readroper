
<!-- README.md is generated from README.Rmd. Please edit that file -->
readroper
=========

[![Build Status](https://travis-ci.org/petulla/readroper.svg?branch=master)](https://travis-ci.org/petulla/readroper)

Use this package to read ASCII fixed-width data files from the Roper Center and other polling providers into R.

Installation
------------

Soon, you can install the released version of readroper from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("readroper")
```

Until then, get the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("petulla/readroper")
```

Usage
-----

To read a multicard ASCII file and weights and output a csv file, just do:

``` r
  weights df <- read_rpr(col_positions=c(1),
               widths=c(3),
               col_names=c('Weights'),
               filepath='data.txt')
   card2 <- read_rpr(col_positions=c(1,2,4), 
               widths=c(1,2,1), 
               col_names=c('V1','V2','V3'), 
               filepath='data.txt', 
               card_read=1, 
               cards=2)
   GALLUP <- cbind(weights,card2)
   GALLUP$Weights = as.numeric(GALLUP$Weights)/100
   write.csv(GALLUP,file='cnngallup.csv', row.names=FALSE)
```

For instructions on use see the [vignette](https://github.com/petulla/readroper/tree/master/vignettes).
