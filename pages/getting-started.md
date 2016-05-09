---
permalink: /getting-started/
layout:    default
title:     Getting Started with the Reproducible Repository
nobio:     true
output: md_document
---

Getting Started
===============

First download the repository to your local machine. If you use Github,
then this will mean cloning the repository into a new R project. If you
are not a Github user, simply click 'Download Zip' and extract the file
to a convenient location.

Repository Contents
-------------------

The repository contains several folders and files. They are organized to
keep data preparation and cleaning in one file, `data-raw`, analysis in
another, `analysis`, and outputs from the analysis that will become
tables and figures, and numbers in the text of the manuscript,
`analysis-output`. The remaining files in the root directory are files
related to the manuscript itself. Next, we'll demonstrate how to link
the raw data to the analysis to the output to the manuscript so that all
the steps to generate the manuscript are automated and thus, not subject
to the inconsistencies that go along with piece-wise data preparation
and analysis.

    + analysis-output
        - results.rda
    + analysis
        - analysis.R
    + data-raw
        - fetch-raw-data.R
    - gitignore
    - README.md
    - README.rmd
    - bibliography.bib
    - manuscript-example.Rmd
    - manuscript-example.pdf
    - research-project-template.Rproj
    - simple.latex
    - style-headers.md
    - tablesandfigures-example.Rmd
    - tablesandfigures-example.pdf

Generate the Manuscript with One Click
======================================

Open the `manuscript-example.Rmd` and `tablesandfigures-examples.Rmd`
files in RStudio. Install the following packages, if they are not
already installed:

    install.packages(xtable)
    install.packages(ggplot2)
    install.packages(ggfortify)
    install.packages(gridExtra)
    install.packages(Quandl)
    install.packages(RCurl)
    install.packages(xts)
    install.packages(urca)
    install.packages(vars)

Click the 'Knit PDF' button on the code editing pane, and voila! A PDF
of the manuscript should appear. In what follows we will walk through
what is happening step by step.
