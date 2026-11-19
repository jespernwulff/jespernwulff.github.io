---
title: "apexog"
weight: 70
pkg_kind: "R package & Stata command"
authors: ["Jesper N. Wulff"]
summary: "Plausibly exogenous bounds for average partial effects (APEs) and average interaction effects (AIEs) in binary-outcome instrumental-variables models."
areas: ["glm", "sensitivity"]
tags: ["instrumental variables", "plausibly exogenous", "sensitivity analysis", "average partial effects", "probit", "R", "Stata"]
related_papers: ["plausibly-exogenous-probit-bounds"]
links:
  - name: "Documentation (R & Stata)"
    url: "https://jespernwulff.github.io/apexog/"
  - name: "GitHub (R)"
    url: "https://github.com/jespernwulff/apexog"
  - name: "GitHub (Stata)"
    url: "https://github.com/jespernwulff/stata-apexog"
---

How large would a violation of the exclusion restriction have to be before the average partial effect from your probit changes sign, or stops being significant? `apexog` carries the plausibly exogenous framework of Conley, Hansen & Rossi (2012) from linear 2SLS coefficients to average partial effects and average interaction effects on the probability scale, estimated by a control-function probit (or, for one binary treatment, a recursive bivariate probit). Results are reported as a union of confidence intervals over a range of assumed violations, or as a local-to-zero interval under a prior.

The R package and the Stata command give the same results and share one [documentation site](https://jespernwulff.github.io/apexog/).

    # R
    # install.packages("remotes")
    remotes::install_github("jespernwulff/apexog")

    * Stata (18 or later)
    net install apexog, from("https://raw.githubusercontent.com/jespernwulff/stata-apexog/main/")
