
<!-- README.md is generated from README.Rmd. Please edit that file -->

# rstudioTeachMode

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/rstudioTeachMode)](https://CRAN.R-project.org/package=rstudioTeachMode)
<!--[![Codecov test coverage](https://codecov.io/gh/murraycadzow/rstudioTeachMode/branch/master/graph/badge.svg)](https://codecov.io/gh/murraycadzow/rstudioTeachMode?branch=master) -->
[![R build
status](https://github.com/murraycadzow/rstudioTeachMode/workflows/R-CMD-check/badge.svg)](https://github.com/murraycadzow/rstudioTeachMode/actions)
<!-- badges: end -->

The goal of rstudioTeachMode is to provide an easy mechanism to switch
between theme preferences for personal use and theme preferences for a
teaching environment.

**This is extremely experimental**

## No installation option:

Insert the following into your `.Rprofile` which can be opened (if you
have `{usethis}` installed) by using `usethis::edit_r_profile()`

``` r
.toggle <- function(){
  # Assumes you are in user mode if first time running in session
  rstudioTeachMode_options <-  getOption("rstudioTeachMode")
  if (is.null(rstudioTeachMode_options)) rstudioTeachMode_options <- list(mode = "user")
  
  # teach -> user
  if (rstudioTeachMode_options$mode == "teach") {
    # select what you want your user settings to be here
    rstudioapi::writeRStudioPreference("font_size_points", 12L) # number has to be integer
    rstudioapi::applyTheme("Solarized Light") # insert name of theme for user here
  } else {# user -> teach
    # select what you want your teaching settings to be
    rstudioapi::writeRStudioPreference("font_size_points", 24L) # number has to be integer
    rstudioapi::applyTheme("Chrome") # insert name of theme for teaching here
  }
  
  # flip the mode in the stored options
  rstudioTeachMode_options$mode <- ifelse(rstudioTeachMode_options$mode == "teach", "user", "teach")
  options(rstudioTeachMode = rstudioTeachMode_options)
}
```

Then you can run `.toggle()` when you want to switch between user and
teaching mode.

## Installation

This package is under development and very experimental but can be
installed from github using - **not recommended at this stage**

``` r
remotes::install_github("murraycadzow/rstudioTeachMode")
```

## Example

This is a basic example which shows you how to solve a common problem:

``` r
library(rstudioTeachMode)
## basic example code
```
