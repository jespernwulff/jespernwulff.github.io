---
title: "bootmakr"
weight: 30
pkg_kind: "R package"
authors: ["Jesper N. Wulff"]
summary: "Bootstrap inference for sensemakr sensitivity analysis."
areas: ["sensitivity"]
tags: ["sensitivity analysis", "bootstrap", "omitted variable bias", "R"]
links:
  - name: "GitHub"
    url: "https://github.com/jespernwulff/bootmakr"
---

`bootmakr` adds bootstrap inference to [sensemakr](https://carloscinelli.com/sensemakr/)-style sensitivity analysis, so that sensitivity statistics come with resampling-based uncertainty rather than point estimates alone. A companion Stata implementation is available as [bootmakr for Stata](../bootmakr-stata/).

    # install.packages("remotes")
    remotes::install_github("jespernwulff/bootmakr")
