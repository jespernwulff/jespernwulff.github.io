---
title: "alphaN"
weight: 10
pkg_kind: "R package"
authors: ["Jesper N. Wulff"]
summary: "Set the significance level as a function of sample size using Bayes factors — a Bayesian-frequentist compromise for significance testing."
areas: ["inference"]
tags: ["significance testing", "Bayes factors", "sample size", "R"]
related_paper: "alpha-sample-size-bayesian-compromise"
links:
  - name: "CRAN"
    url: "https://cran.r-project.org/package=alphaN"
  - name: "GitHub"
    url: "https://github.com/jespernwulff/alphaN"
---

`alphaN` implements the Bayesian–frequentist compromise from Wulff & Taylor (2024): it returns a sample-size-dependent significance threshold derived from Bayes factors, so that the alpha level shrinks as the sample grows. An interactive web app built on the same method lets users explore thresholds without writing code.

    install.packages("alphaN")
    library(alphaN)
    alphaN(n = 500)
