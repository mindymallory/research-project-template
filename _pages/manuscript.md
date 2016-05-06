---
permalink: /manuscript/
layout:    default
title:     Manuscript
nobio:     true
output: md_document
---

The Manuscript
--------------

At the top of the file named `manuscript-example.Rmd` you see a YAML
(Yet Another Mark Up Language) header. This header tells knitr and
pandoc what exactly you want done with the document.

    ---
    title: "A Very Serious Analysis of the Stationarity of Corn and Soybean Prices"
    author: "Peter Economist, Paul Economist, Mary Economist"
    date: 'May 05, 2016'
    output: 
      pdf_document:
        template: simple.latex
        fig_caption: yes
    documentclass: ajae
    bibliography: bibliography.bib
    ---

`Title` and `author` are self explanatory.

`date`: field tells knitr to place the current date formatted in the
`%B %d, %Y` style.

`output`: After knitr evaluates code chunks contained in the body of the
file. The output feild tells pandoc what kind of file to create. Here we
have specified to produce PDF output. PDF output is produced by pandoc
creating a `.tex` file and if no further fields are specified there is a
latex template that pandoc uses to make the docuement (based on the
`article` class). Here we have specified to create the manuscript
according to the specifications of the American Journal of Agricultural
Economics (AJAE). Since they have their own latex class (`ajae`) that
comes in the standard latex distribution we can just specify
`documentclass: ajae` and the formatting is handled. We needed to also
specify `template: simple.latex` because something in the pandoc
template was clashing with the `ajae.csl` file. I removed the problem
lines and saved that as `simple.latex`, which you can see in the root
directory of this repository. We will cover how to specify different
output formats in a later section.

`bibliography`: The file `bibliography.bib` is located in the root
directory of this repository and it is a Bibtex database of all the
references needed for the manuscript. Open this file and note what the
reference entries look like. To build a database for your own paper,
Google Scholar has a 'cite' button below every search result it returns.
Click 'cite', then click 'Bibtex' and a plain text window will open with
the properly formatted Bibtex entry. Just copy and paste this into
`bibliography.bib`. The `bibliography.bib` file used for this tutorial is shown below. 

    @article{akerlof1970vthe,
    title={The Market for Lemons: Qualitative Uncertainty and the Market MechanismV},
    author={Akerlof, George},
    journal={Quarterly Journal of Economics},
    volume={84},
    year={1970}
    }

    @article{johansen1988statistical,
    title={Statistical analysis of cointegration vectors},
    author={Johansen, S{\o}ren},
    journal={Journal of economic dynamics and control},
    volume={12},
    number={2},
    pages={231--254},
    year={1988},
    publisher={Elsevier}
    }

    @article{said1984testing,
    title={Testing for unit roots in autoregressive-moving average models of unknown order},
    author={Said, Said E and Dickey, David A},
    journal={Biometrika},
    volume={71},
    number={3},
    pages={599--607},
    year={1984},
    publisher={Biometrika Trust}
    }

    @book{enders1995applied,
    title={Applied Econometric Time Series },
    author={Enders, Walter},
    year={1995},
    publisher={Applied Economic Time Series}
    }

    @book{gandrud2013reproducible,
    title={Reproducible Research with R and R Studio},
    author={Gandrud, Christopher},
    year={2013},
    publisher={CRC Press}
    }

