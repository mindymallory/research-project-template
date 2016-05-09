---
permalink: /markdown/
layout:    default
title:     Markdown
nobio:     true
output: md_document
---

# Markdown Basics

Formatting a docuemnt with Markdown is very easy and there are many
resources to learn the basics. Start with
[<http://rmarkdown.rstudio.com/index.html>](http://rmarkdown.rstudio.com/index.html)
and explore.

Main points:

    # This is a Level 1 Header

This is a Level 1 Header
========================

    ## This is a Level 2 Header

This is a Level 2 Header
------------------------

    This is a citation of Akerlof's Lemons paper [@akerlof1970vthe].

This is a citation of Akerlof's Lemons paper (Akerlof 1970).

### Code Chunks

This is an example of a code chunk that is in the manuscript document.
The opening line tells `knitr` that what follows is code chunk to be
evaluated.

     ``{r, echo=FALSE, warning = FALSE, message = FALSE, results = "asis"}
     t = list()
     t[[1]] <- xtable(adf[[1]]@testreg, caption = "ADF Results for Corn")
     t[[2]] <- xtable(adf[[2]]@testreg, caption = "ADF Results for Soybeans")
     print.xtable(t[[1]], caption.placement = 'top', comment = FALSE)
     ``

In the opening code chunk, we specify that we want to load the results
from the `analysis-output` folder and we also want to fetch the raw
data, which we will plot in a later code chunk. Also, we load all the
libraries that will be used by later code chunks.

    ``{r, warning = FALSE, message = FALSE, echo=FALSE}
    library(xtable)
    library(ggplot2)
    library(ggfortify)
    library(gridExtra)
    source('data-raw/fetch-raw-data.R')
    load('analysis-output/results.Rda')
    
References
==========

Akerlof, George. 1970. “The Market for Lemons: Qualitative Uncertainty
and the Market MechanismV.” *Quarterly Journal of Economics* 84.

Gandrud, Christopher. 2013. *Reproducible Research with R and R Studio*.
CRC Press.

Said, Said E, and David A Dickey. 1984. “Testing for Unit Roots in
Autoregressive-Moving Average Models of Unknown Order.” *Biometrika* 71
(3). Biometrika Trust: 599–607.
