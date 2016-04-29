-   Research Project Template
-   Getting Started
    -   Repository Contents
-   Generate the Manuscript with One Click
-   Putting it all Together
    -   The `data-raw` Folder
    -   The `analysis` Folder
    -   The `analysis-output` Folder

Research Project Template
=========================

This repository contains a template for a reproducable research project.
The fundamental idea of reproducable research is that the steps that
take your research from raw data to manuscript, thesis, or report should
be fully automated. This way, your work can be checked by your advisor,
mentors, collaborators, others working in your area, journal reviewers,
and your future self.

I became interested in reproducable research because I was tired of
being terrified of my own analysis. I was constantly petrified someone
would question my work and ask me to open the black box and verify what
I did was correct; in some cases even being asked reproduce a result was
terrifiying because I knew the convoluted path of data prep and cleaning
that I took in arriving at my result.

I read the book [Reproducable Research with R and
RStudio](http://www.amazon.com/Reproducible-Research-Studio-Chapman-Hall/dp/1466572841)
by Christopher Gandrud (2013), and I read a lot of blog posts and
tutorials by [Karl Broman](http://kbroman.org/pages/software.html) and
[Carl
Boettiger](http://www.carlboettiger.info/2012/05/06/research-workflow.html)
and I struck out on my own path to execute a reproducable research
project from start to finish. The repository for that project is
[here](https://github.com/mindymallory/BBOBAS), while I was successful
in learning the basics of how r, rmarkdown, knitr, and pandoc combine to
make reproducable research possible, you can tell just by looking at the
project's Github repository that I failed miserably at making the
project reproducable. This is because the repository is totally
unorganized, and I am pretty sure I am the only one who could reproduce
the results from this project.

But in that failure, I learned a lot about how a reproducable research
project should be organized. I built this template for my future
students and for my future self.

Getting Started
===============

First download the repository to your local machine. If you use Github,
then this will mean cloning the repository into a new R project. If you
are not a Github user, simply click 'Download Zip' and extract the file
to a convenient location.

Repository Contents
-------------------

The repository contains several folders and files. They are organized to
keep data preperation and cleaning in one file, `data-raw`, analysis in
another, `analysis`, and outputs from the analysis that will become
tables and figures, and numbers in the text of the manuscript,
`analysis-output`. The remaining files in the root directory are files
related to the manuscript itself. Next, we'll demonstrate how to link
the raw data to the analysis to the output to the manuscript so that all
the steps to generate the manuscript are automated and thus, not subject
to the inconsistencies that go along with peice-wise data preparation
and analysis.

Generate the Manuscript with One Click
======================================

Open the `manuscript-example.Rmd` and `tablesandfigures-examples.Rmd`
files in RStudio. Click the 'Knit PDF' button on the code editing pane.
Install the following packages, if they are not already installed:

    install.packages(xtable)
    install.packages(ggplot2)
    install.packages(ggfortify)
    install.packages(gridExtra)
    install.packages(Quandl)
    install.packages(RCurl)
    install.packages(xts)
    install.packages(urca)
    install.packages(vars)

Click the 'Knit PDF' button on the code editing pane.

Putting it all Together
=======================

Now we see the contents of the data and analysis files and how they come
together.

The `data-raw` Folder
---------------------

The `data-raw` folder should either contain your raw data files (that
will **never** *ever* be modified), or a script that makes and api call,
or pulls the raw data in from a shared server, etc. In this example
file, there is a script called `fetch-raw-data.R`, and its contents are
shown below. This file fetches corn and soybean price data from
[quandl.com](quandl.com) and puts them in data objects called
`CZ2016 and SX2016`. Then it converts the data to `xts` objects, and
trims the dates to the study period of interest.

    # Filename: fetch-raw-data.R
    # This file fetches the raw data and performs pre-processing (cleaning) to get it ready for analyzs

    library(RCurl)
    library(xts)

    # Define Dates of Analysis
      start  <- '2015-01-01'
      today  <- format(Sys.time(),"%Y-%m-%d")

    # Fetch Corn and Soybean Prices
      CZ2016 <- getURL("https://www.quandl.com/api/v1/datasets/CME/CZ2016.csv")
      SX2016 <- getURL("https://www.quandl.com/api/v1/datasets/CME/SX2016.csv")

      CZ2016 <- read.csv(text = CZ2016)
      SX2016 <- read.csv(text = SX2016)

    # Define first column to be a date.
      CZ2016[,1] <- as.Date(CZ2016[,1])
      SX2016[,1] <- as.Date(SX2016[,1])

    # Define the data objects to be xts objects, and keep only settlement prices
      CZ2016 <- xts(CZ2016[,'Settle'], order.by=CZ2016[,1])
      SX2016 <- xts(SX2016[,'Settle'], order.by=SX2016[,1])

    # Trim the dates
      CZ2016 <- CZ2016[paste0(start,'/',today)]
      SX2016 <- SX2016[paste0(start,'/',today)]

Of course, every data cleaning and preparation activity will be
different, but in this file you should do all the preparation so that
the objects created by this script are ready to be accepted in the
`analysis.R` script.

The `analysis` Folder
---------------------

The contents of the `analysis` folder are below. The key is the line
that says, `source('data-raw/fetch-raw-data.R')`. This calls the
`fetch-raw-data.R` script so that when you run the code below, the raw
data are fetched and prepared (from scratch each time you run the
script). Then, the following contents of the `analysis.R` script test
the corn and soybean prices for the presence of unit roots via the ADF
test (Said and Dickey 1984).

    # Filename: analysis.R
    # This file performs statistical analysis. It could be just one file, so it doesn't neccessarly 
    #  need it's own folder, but sometimes your analysis may get complicated enough that you want 
    # to compartmentalize it. Separating different types of analyses into different scripts contained
    #  in the same folder can facilitate this

    library(urca)
    library(vars)
    # This line runs the source code that fetched your raw data and cleaned it. Now it is available 
    # for conducting analysis.
    source('data-raw/fetch-raw-data.R')

    # Store results of ADF tests for Corn and Soybeans in a list
    adf      <- list()
    adf[[1]] <- ur.df(CZ2016, type = 'drift', lags = 5)
    adf[[2]] <- ur.df(SX2016, type = 'drift', lags = 5) 


    # Store results of a Johansen cointegration test for Corn and Soybeans 
    jct      <- ca.jo(cbind(CZ2016, SX2016), type = 'eigen', K = 5)


    # Fit a VAR

    lag_selection <- VARselect(cbind(CZ2016, SX2016), lag.max = 8)

    var_model <- VAR(cbind(CZ2016, SX2016), p = 1, type = "const")

    # Save these results so that it can be pulled into the manuscript without re-running analysis.
    save(adf, jct, lag_selection, var_model, file = 'analysis-output/results.rda')

The `analysis-output` Folder
----------------------------

The last line of the code snippet above says,
`save(adf, jct, lag_selection, var_model, file = 'analysis-output/results.rda')`.
What this does is save the objects that contain the adf, Johansen
cointegration, and VAR regression results to an `.rda` file called
`results.rda` in the `analysis` folder. This 'R Data' file can be read
in by R and the variable names, `adf`, `jct`, `lag_selection`, and
`var_model` are preserved when loaded later. We will load the
`results.rda` file into the `tablesandfigures-example.Rmd` document to
make tables and figures in the manuscript.

References
==========

Gandrud, Christopher. 2013. *Reproducible Research with R and R Studio*.
CRC Press.

Said, Said E, and David A Dickey. 1984. “Testing for Unit Roots in
Autoregressive-Moving Average Models of Unknown Order.” *Biometrika* 71
(3). Biometrika Trust: 599–607.
