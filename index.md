---
layout: page
title: Tutorial
tagline: 
description: Minimal tutorial on writing a reproducible manuscript with R, and RStudio
output: md_document
bibliography: bibliography.bib
---

<!-- After knitting, paste the yaml header above  -->

Introduction
------------

The Github repository located
[here](https://github.com/mindymallory/research-project-template)
contains a template for a reproducible research project. The fundamental
idea of reproducible research is that the steps that take your research
from raw data to manuscript, thesis, or report should be fully
automated. This way, your work can be checked by your adviser, mentors,
collaborators, others working in your area, journal reviewers, and your
future self.

R and RStudio are an excellent vehicle for conducting reproducible
research. You write manuscripts and reports in `.rmarkdown` documents
that includes code chunks that perform analysis. The code chunks are
evaluated by `R` and incorporated in the document by the tools in the
`knitr` package to produce a markdown `.md` document. From there a
program called `pandoc` converts your markdown document to whatever file
format you like: PDF (formatted with latex .csl files), html, or
Microsoft Word. This all happens without the user really knowing what is
going on, which makes it easy to get started.

Table of Contents
-----------------

[Introduction to R](/research-project-template/intro-to-r)  
[Getting Started](/research-project-template/getting-started)  
[Data](/research-project-template/data-raw)  
[Analysis](/research-project-template/analysis)  
[Manuscript](/research-project-template/manuscript)  
[Markdown](/research-project-template/markdown)  
[Latex](/research-project-template/latex)  
[If Your Collaborators Use Word](/research-project-template/need-word)  
[Your Own Reproducible Research Prject](on-your-own)  
[Download Repository
Contents](https://github.com/mindymallory/research-project-template/tree/master)

On Your Own
-----------

Once you understand how all the peices fit together you can modify these
files to conduct your own reproducable project. Just make sure your
`data-raw` is accessed by your analysis scripts and that your results
are stored in the `anlaysis-output` folder. Then make sure your
manuscript pulls the data and analysis results automatically.

Background
----------

I became interested in reproducible research because I was tired of
being terrified of my own analysis. I was constantly petrified someone
would question my work and ask me to open the black box and verify what
I did was correct; in some cases even being asked reproduce a result was
terrifying because I knew the convoluted path of data prep and cleaning
that I took in arriving at my result.

I read the book [Reproducable Research with R and
RStudio](http://www.amazon.com/Reproducible-Research-Studio-Chapman-Hall/dp/1466572841)
by Christopher Gandrud (2013), and I read a lot of blog posts and
tutorials by [Karl Broman](http://kbroman.org/pages/software.html) and
[Carl
Boettiger](http://www.carlboettiger.info/2012/05/06/research-workflow.html)
and I struck out on my own path to execute a reproducible research
project from start to finish. The repository for that project is
[here](https://github.com/mindymallory/BBOBAS), while I was successful
in learning the basics of how r, rmarkdown, knitr, and pandoc combine to
make reproducible research possible, you can tell just by looking at the
project's Github repository that I failed miserably at making the
project reproducible. This is because the repository is totally
unorganized, and I am pretty sure I am the only one who could reproduce
the results from this project.

But in that failure, I learned a lot about how a reproducible research
project should be organized. I built this template for my future
students and for my future self.

References
----------

Gandrud, Christopher. 2013. *Reproducible Research with R and R Studio*.
CRC Press.
