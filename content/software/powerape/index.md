---
title: "powerape"
weight: 60
pkg_kind: "R package & Stata command"
authors: ["Jesper N. Wulff"]
summary: "Power analysis when the effect of interest is an average partial effect (APE) or average interaction effect (AIE) from a probit or logit model, stated in probability points."
areas: ["glm"]
tags: ["power analysis", "average partial effects", "interaction effects", "logit", "probit", "R", "Stata"]
links:
  - name: "Documentation (R & Stata)"
    url: "https://jespernwulff.github.io/powerape/"
  - name: "GitHub (R)"
    url: "https://github.com/jespernwulff/powerape"
  - name: "GitHub (Stata)"
    url: "https://github.com/jespernwulff/powerape-stata"
---

In a probit or logit model the coefficient is not the quantity anyone interprets: conclusions are stated in probability points, as the average partial effect (APE) or, for a moderation question, the average interaction effect (AIE). `powerape` takes the effect in those units and answers the practical question: *how many observations do I need to show an effect of, say, five percentage points?*

It simulates the whole study (draw the data, fit the model, compute the effect with a delta-method confidence interval) and reports power for three claims on that interval (Riesthuis, 2024): that the effect exceeds the smallest effect size of interest, that it differs from zero, or that it is too small to matter. It also gives required sample sizes, minimum detectable effects, robustness sweeps over contextual assumptions, and justified alpha levels.

The R package and the Stata command implement the same procedure and share one [documentation site](https://jespernwulff.github.io/powerape/).

    # R
    # install.packages("remotes")
    remotes::install_github("jespernwulff/powerape")

    * Stata (16 or later)
    net install powerape, from("https://raw.githubusercontent.com/jespernwulff/powerape-stata/main/")
    mata: mata mlib index
