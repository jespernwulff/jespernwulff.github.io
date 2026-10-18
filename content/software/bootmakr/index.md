---
title: "bootmakr"
weight: 30
pkg_kind: "R package"
authors: ["Jesper N. Wulff"]
summary: "Bootstrap inference for sensemakr sensitivity analysis."
areas: ["sensitivity"]
tags: ["sensitivity analysis", "bootstrap", "omitted variable bias", "R"]
related_paper: "itcv-robust-standard-errors"
links:
  - name: "Documentation (R & Stata)"
    url: "https://jespernwulff.github.io/bootmakr/"
  - name: "GitHub"
    url: "https://github.com/jespernwulff/bootmakr"
---

`bootmakr` adds bootstrap inference to [sensemakr](https://carloscinelli.com/sensemakr/)-style sensitivity analysis, so that sensitivity statistics come with resampling-based uncertainty rather than point estimates alone. It accompanies Lonati & Wulff (2026). A companion Stata implementation is available as [bootmakr for Stata](../bootmakr-stata/).

The R package and the Stata command share one [documentation site](https://jespernwulff.github.io/bootmakr/), with getting-started guides for both, a worked example, and the argument for the bootstrap.

    # install.packages("remotes")
    remotes::install_github("jespernwulff/bootmakr")
