---
title: "bootmakr"
weight: 30
pkg_kind: "R package & Stata command"
authors: ["Jesper N. Wulff"]
summary: "Bootstrap inference for sensemakr sensitivity analysis, including clustered bootstrap and benchmark covariates."
areas: ["sensitivity"]
tags: ["sensitivity analysis", "bootstrap", "omitted variable bias", "R", "Stata"]
related_paper: "itcv-robust-standard-errors"
aliases: ["/software/bootmakr-stata/"]
links:
  - name: "Documentation (R & Stata)"
    url: "https://jespernwulff.github.io/bootmakr/"
  - name: "GitHub (R)"
    url: "https://github.com/jespernwulff/bootmakr"
  - name: "GitHub (Stata)"
    url: "https://github.com/jespernwulff/bootmakr-stata"
---

`bootmakr` adds bootstrap inference to [sensemakr](https://carloscinelli.com/sensemakr/)-style sensitivity analysis, so that sensitivity statistics come with resampling-based uncertainty rather than point estimates alone. For an omitted variable as strong as an observed benchmark covariate, it reports the bias-adjusted coefficient with a bootstrap standard error, percentile confidence interval, and *p*-value, resampling observations, whole clusters, or units within strata. It accompanies Lonati & Wulff (2026).

The R package and the Stata command implement the same procedure and share one [documentation site](https://jespernwulff.github.io/bootmakr/), with getting-started guides for both, a worked example, and the argument for the bootstrap.

    # R
    # install.packages("remotes")
    remotes::install_github("jespernwulff/bootmakr")

    * Stata
    ssc install sensemakr
    net install bootmakr, from("https://raw.githubusercontent.com/jespernwulff/bootmakr-stata/main/")
