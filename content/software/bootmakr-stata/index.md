---
title: "bootmakr for Stata"
weight: 40
pkg_kind: "Stata package"
authors: ["Jesper N. Wulff"]
summary: "Bootstrap inference for sensemakr sensitivity analysis in Stata, including clustered bootstrap and benchmark covariates."
areas: ["sensitivity"]
tags: ["sensitivity analysis", "bootstrap", "omitted variable bias", "Stata"]
related_paper: "itcv-robust-standard-errors"
links:
  - name: "Documentation (R & Stata)"
    url: "https://jespernwulff.github.io/bootmakr/"
  - name: "GitHub"
    url: "https://github.com/jespernwulff/bootmakr-stata"
---

The Stata implementation of [bootmakr](../bootmakr/): bootstrap inference for `sensemakr` sensitivity analysis, with support for clustered bootstrap, benchmark covariates, multiple `kd` values, and plots.

The Stata command and the R package share one [documentation site](https://jespernwulff.github.io/bootmakr/), with getting-started guides for both, a worked example, and the argument for the bootstrap.

    ssc install sensemakr
    net install bootmakr, from("https://raw.githubusercontent.com/jespernwulff/bootmakr-stata/main/")
