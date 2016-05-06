---
permalink: /introduction/
layout:    default
title:     Reproducable Research Project Template
nobio:     true
---

# Introduction

The Github repository located [here](https://github.com/mindymallory/research-project-template) contains a template for a reproducible research project. The fundamental idea of reproducible research is that the steps that take your research from raw data to manuscript, thesis, or report should be fully automated. This way, your work can be checked by your adviser, mentors, collaborators, others working in your area, journal reviewers, and your future self. 

R and RStudio are an excellent vehicle for conducting reproducible research. You write manuscripts and reports in `.rmarkdown` documents that includes code chunks that perform analysis. The code chunks are evaluated by `R` and incorporated in the document by the tools in the `knitr` package to produce a markdown `.md` document. From there a program called `pandoc` converts your markdown document to whatever file format you like: PDF (formatted with latex .csl files), html, or Microsoft Word. This all happens without the user really knowing what is going on, which makes it easy to get started.    
