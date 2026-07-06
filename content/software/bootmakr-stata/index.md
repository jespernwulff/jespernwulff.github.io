---
title: "bootmakr for Stata"
weight: 40
pkg_kind: "Stata package"
authors: ["Jesper N. Wulff"]
summary: "Bootstrap inference for sensemakr sensitivity analysis in Stata, including clustered bootstrap and benchmark covariates."
areas: ["sensitivity"]
tags: ["sensitivity analysis", "bootstrap", "omitted variable bias", "Stata"]
links:
  - name: "GitHub"
    url: "https://github.com/jespernwulff/bootmakr-stata"
---

The Stata implementation of [bootmakr](../bootmakr/): bootstrap inference for `sensemakr` sensitivity analysis, with support for clustered bootstrap, benchmark covariates, multiple `kd` values, and plots.

    net install bootmakr, from("https://raw.githubusercontent.com/jespernwulff/bootmakr-stata/main/")
