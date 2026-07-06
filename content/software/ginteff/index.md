---
title: "ginteff"
weight: 50
pkg_kind: "R package"
authors: ["Jesper N. Wulff"]
summary: "Two- and three-way interaction effects for fitted regression models, with delta-method standard errors — an R port of Marius Radean's Stata command."
areas: ["glm"]
tags: ["interaction effects", "marginal effects", "generalized linear models", "R"]
links:
  - name: "GitHub"
    url: "https://github.com/jespernwulff/ginteff"
---

`ginteff` is an R port of the Stata [ginteff](https://doi.org/10.1177/1536867X231175253) command by Marius Radean (*The Stata Journal*, 2023). It computes two- and three-way interaction effects — via partial derivatives or first differences — for fitted regression models, with delta-method standard errors.

Built as a thin wrapper around [marginaleffects](https://marginaleffects.com), it supports arbitrary variance–covariance specifications (`"HC3"`, clustered, or a user-supplied sandwich matrix), which propagate through to the final interaction-effect standard errors.

    # install.packages("remotes")
    remotes::install_github("jespernwulff/ginteff")
