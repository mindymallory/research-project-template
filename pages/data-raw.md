---
permalink: /data-raw/
layout:    default
title:     Data
nobio:     true
output: md_document
---


The `data-raw` Folder
---------------------

Now we see the contents of the data and analysis files and how they come
together. The `data-raw` folder should either contain your raw data
files (that will **never** *ever* be modified), or a script that makes
and api call, or pulls the raw data in from a shared server, etc. In
this example file, there is a script called `fetch-raw-data.R`, and its
contents are shown below. This file fetches corn and soybean price data
from [quandl.com](quandl.com) and puts them in data objects called
`CZ2016 and SX2016`. Then it converts the data to `xts` objects, and
trims the dates to the study period of interest.

    # Filename: fetch-raw-data.R
    # This file fetches the raw data and performs pre-processing (cleaning) to get it ready for analyzs

    library(RCurl)
    library(xts)
    library(Quandl)
    Quandl.api_key("79SfoMaQc1npRAuq9ExZ")
    # Define Dates of Analysis
      start  <- '2015-01-01'
      today  <- format(Sys.time(),"%Y-%m-%d")

    # Fetch Corn and Soybean Prices
      CZ2016 <- Quandl("CME/CZ2016", type = "xts")
      SX2016 <- Quandl("CME/SX2016", type = "xts")

    # Trim the dates
      CZ2016 <- CZ2016[paste0(start,'/',today), 'Settle']
      SX2016 <- SX2016[paste0(start,'/',today), 'Settle']

Of course, every data cleaning and preparation activity will be
different, but in this file you should do all the preparation so that
the objects created by this script are ready to be accepted in the
`analysis.R` script.
