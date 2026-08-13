---
title: "Decomposing Price Chart Signals in Return Prediction"
date: 2026-07-14
authors: ["Jonas Theill Bøjstrup", "Bezirgen Veliyev", "Jesper N. Wulff"]
publication_types: ["article"]
publication: "Review of Financial Studies"
journal: "Review of Financial Studies"
url_preprint: "https://ssrn.com/abstract=7119420"
status: "under_review"
tab: "under-review"
areas: ["deeplearning"]
tags: ["candlestick charts", "deep learning", "return prediction"]
abstract: "Image models trained on stock charts predict returns out of sample, though a chart adds no information beyond the OHLCV data it renders. We decompose the image model's advantage over tabular benchmarks from the same daily window into three sources: function-class capacity, chart-specific encoding, and how each model smooths noisy returns. Capacity contributes little. Under a distillation accounting, roughly 60% of the apparent gap is tied to learning from noisy realized returns rather than chart-specific content. The residual localizes to recent bars, intraday extremes, and temporal order, and is largely recoverable with explicit predictors."
---
