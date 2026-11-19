---
title: "alphaN"
weight: 10
pkg_kind: "R package & Stata command"
authors: ["Jesper N. Wulff"]
summary: "Set the significance level as a function of sample size using Bayes factors — a Bayesian-frequentist compromise for significance testing."
areas: ["inference"]
tags: ["significance testing", "Bayes factors", "sample size", "R", "Stata"]
related_papers: ["alpha-sample-size-bayesian-compromise"]
# When the R Journal paper (Taylor & Wulff, "alphaN: Calibrating Significance Levels to Bayes Factors for Regression Models in R") is online, add its publication slug to related_papers.
links:
  - name: "Documentation (R & Stata)"
    url: "https://jespernwulff.github.io/alphaN/"
  - name: "CRAN"
    url: "https://cran.r-project.org/package=alphaN"
  - name: "GitHub (R)"
    url: "https://github.com/jespernwulff/alphaN"
  - name: "GitHub (Stata)"
    url: "https://github.com/jespernwulff/alphaN-stata"
---

`alphaN` implements the Bayesian–frequentist compromise from Wulff & Taylor (2024): it returns a sample-size-dependent significance threshold derived from Bayes factors, so that the alpha level shrinks as the sample grows. It also computes Bayes factors for the coefficients of a fitted model, power at the calibrated level, and a report for preregistrations. An interactive web app built on the same method lets users explore thresholds without writing code.

The R package and the Stata command (`alphan`) give the same results and share one [documentation site](https://jespernwulff.github.io/alphaN/).

    # R
    install.packages("alphaN")
    library(alphaN)
    alphaN(n = 500)

    * Stata (14 or later)
    net install alphan, from("https://raw.githubusercontent.com/jespernwulff/alphaN-stata/main/")
    alphan 1000, bf(3)
