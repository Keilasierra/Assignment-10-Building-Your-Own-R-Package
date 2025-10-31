# Assignment-10-Building-Your-Own-R-Package
# Install and load required tools
install.packages(c("devtools","usethis","roxygen2","testthat"))

# Create my package plot
devtools::create("Friedman")

#double checking my work
getwd()

# Set up project structure and license
library(usethis)
use_roxygen_md()
use_license("CC0")
use_package("ggplot2")
use_package("dplyr")


# Create the R file for the scale01 function
usethis::use_r("scale01")


#Trial function
scale01 <- function(x) {
  rng <- range(x, na.rm = TRUE)
  if (diff(rng) == 0) return(rep(0, length(x)))
  (x - rng[1]) / diff(rng)
}

# Generate documentation and NAMESPACE
devtools::check()

# Checking that the package builds correctly
devtools::build()
