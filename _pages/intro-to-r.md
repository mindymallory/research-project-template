---
permalink: /intro-to-r/
layout:    default
title:     Introduction to R
nobio:     true
output: md_document
bibliography: bibliography.bib
---
---
permalink: /intro-to-r/
layout:    default
title:     Introduction to R
nobio:     true
output: md_document
bibliography: bibliography.bib
---

Getting Started with R and RStudio
==================================

We will walk through a short introduction to R and RStudio. There are
many free and comprehensive tutorials available on the web, so our focus
here will be to introduce only the concepts and functionality that we
need to get started with price analysis as quickly as possible. Readers
who come to this book because they want to do price analysis
professionally using R will probably want to go back and learn R in a
more comprehensive way after they have finished *Commodity Price
Analysis* and the *R Companion*. At the end of this chapter I list some
excellent tutorials available for free on the web, and there are many
more not listed here.

Background
----------

For history on the development of R,
[Wikipedia](https://en.wikipedia.org/wiki/R_(programming_language)) is
probably the best source.

> R is a programming language and software environment for statistical
> computing and graphics. The R language is widely used among
> statisticians and data miners for developing statistical software and
> data analysis. ... R is an implementation of the S programming
> language combined with lexical scoping semantics inspired by Scheme. S
> was created by John Chambers while at Bell Labs. There are some
> important differences, but much of the code written for S runs
> unaltered. R was created by Ross Ihaka and Robert Gentleman at the
> University of Auckland, New Zealand, and is currently developed by the
> R Development Core Team, of which Chambers is a member. R is named
> partly after the first names of the first two R authors and partly as
> a play on the name of S. R is a GNU project. The source code for the R
> software environment is written primarily in C, Fortran, and R. R is
> freely available under the GNU General Public License, and
> pre-compiled binary versions are provided for various operating
> systems. R uses a command line interface; there are also several
> graphical front-ends for it. [Source:
> Wikipedia](https://en.wikipedia.org/wiki/R_(programming_language))

R as an open source project has been developed for decades now - which
means people have written solutions and made them available for free for
all kinds of problems related to statistics, programming, analytics and
much more. Whatever kind of work you want to do related to statistics,
there is a good chance someone has already done the hard work for you.
All you have to do is find it and figure out how to implement it. For
price analysis, we will cover the basics here.

R by itself functions through a command line interface, which is not
very convenient unless you are very technically inclined. Thankfully,
there are several Graphical interfaces (called integrated development
environments (IDE)) which makes life a lot easier. Some key
functionality is available through clickable menus and viewing panes -
just like the vast majority of software we are used to interacting with.
My favorite is RStudio, and it is what we will use throughout this book.

If you do not have any background programming, this may all sound
daunting. Believe me, using R and RStudio is more accessible than it
sounds. Let jump right in and get started. Since R and RStudio are open
source, it is available for free to download.

Download R
----------

Go to [<https://www.r-project.org/>](https://www.r-project.org/), where
the software is available for downloading.

![Screenshot of r-project.org](/images/Rpojectsite.jpg)

Click "download R", and scroll to a server mirror close to you. It does
not matter much which one you choose; mirrors that are physically closer
to you will produce downloads marginally faster, but if you are in the
United States, for example, and you choose any of the mirrors located in
the United States, you are not likely to notice a difference.

When you click a mirror you will see a screen like the following:

![Screenshot of R Download Links](/images/rdownload.jpg)

Click the link for your appropriate operating system, and click "base"
on the next screen. Finally, if you are running windows you will see the
following screen:

![Screenshot of Windows .exe Download Links](/images/windowsexe.jpg)

Click the *Download R 3.2.1 for Windows* link and run the installation
file. Note that the release number may be different since new releases
of the software periodically come out. Now you have R installed! Now we
will install RStudio.

Download RStudio
----------------

Downloading RStudio is a bit easier. Go to
[<https://www.rstudio.com/products/rstudio/download/>](https://www.rstudio.com/products/rstudio/download/)
and the download links are on one page for all supported operating
systems. Click your operating system and run the installation file.

![Screenshot of RStudio Download Links](/images/downloadrstudio.jpg)

Congratulations, you now have R and RStudio installed!

Orienation to the RStudio IDE
-----------------------------

Now we will get acquainted with the RStudio IDE. First open RStudio. You
will see the main window pane divided into three sections. The large
pane on the left is called the *Console*. It is where commands can be
executed within R. In the upper right corner is a pane with
*Environment* and *History* tabs. The environment will show you what
data or variables have been saved into the environment. Since we have
not done anything, this is empty. In history tab, a record of every
command given in the console is kept.

The lower right hand corner holds several tabs: *Files*, *Plots*,
*Packages*, *Help*, and *Viewer*. More on these things later.

![Screenshot of RStudio](/images/rstudio.png)

The power of R, is not in the line by line execution of commands, it is
in writing scripts were commands can be stored and reused. In the upper
left hand corner of RStudio, is an icon just below the *File* menu.
Clicking it reveals a menu to open different kinds of script templates.
Click it and choose *R Script*. The R script will open in the RStudio
window and now there are four panes open. Let's assign the value `2` to
a variable called `x` and the value `3` to a variable called `y`. Then
we will add them together and store the result as `z`. This is done by
using the characters `<-` together to assign the values to the variable
names. Type the following into the R script.

    x <- 2
    y <- 3
    z <- x+y
    z

    ## [1] 5

Click on the *Environment* tab in the upper right hand corner. You will
see `x, y, and z` and their values. In this book, notice that output
from R is preceded by '\#\#'. The hashtag symbol indicates comments to
R, so anything to the right of a comment will not be evaluated. This
facilitates copy and pasting from this document into the R console,
since only the intended input will be evaluated.

For the exercises that follow, type your commands into the R script file
to save them for reference. In the top right of the script pane you see
a button labeled 'Run'. If you click it R will execute whatever line of
code you are on. Pressing `Ctrl+Enter` does the same. If you click
'Source', just to the right of 'Run', R will execute the entire file.

Please create a folder on your computer labeled 'Chapter1' and save this
R script with the name Chapter1.R.

Basic Calculations
------------------

In the Console type the following to get acquainted with performing
arithmetic in R.

    2+2

    ## [1] 4

    6*7

    ## [1] 42

    12/4

    ## [1] 3

    5^2

    ## [1] 25

    sqrt(2)

    ## [1] 1.414214

    log(100)

    ## [1] 4.60517

    exp(4.60517)

    ## [1] 99.99998

    exp(log(100))

    ## [1] 100

Datatypes
---------

When you assign variables or load data into R, it is defined as one of
several datatypes that have specific attributes. Some basic familiarity
with R's datatypes is necessary because all R functions expect the
inputs to be of certain datatypes, and will not run if you give it a
character when it is expecting an integer, for example.

### Numeric, Integer, and Character, and Logical

The first four are pretty straightforward. The *Numeric* datatype is for
floating decimal, like 2.34. *Integer* variables must be whole numbers,
and *Character* variables must be character strings like
`"Hello World"`. Logicals are either `TRUE` or `FALSE`.

### Vector

A vector is a datatype that is a sequence of elements of the same type
(enumerated above).

A vector of numeric elements

    x <- c(2.3, 4, 6, -10)

The function, `c()` is the concatenate function. It just takes the
elements between the comma's and puts them together in one matrix.

A vector of character elements

    y <- c("Hello", "My", "Name", "Is")

A vector of logical elements

    z <- c(FALSE, FALSE, FALSE, TRUE, TRUE, FALSE, TRUE)

### Matrix

Matrices are simply two dimensional vectors. Since we need to specify
how the dimensions work, we will use a specific function for defining a
matrix.

    z <- matrix(c(1,2,3,4,5,6), nrow = 3, ncol=2)
    z

    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6

    z <- matrix(c(1,2,3,4,5,6), nrow = 2, ncol=3)
    z

    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6

It takes a vector one one dimension and allocates it to rows and columns
as you define in the function arguments. The datatypes of the elements
of a matrix must be the same type, as is true for vectors.

### List

A list is kind of like a vector, except its elements can be of different
types.

    list1 <- list(x, y, z, 22, "R is really fun to learn")
    list1

    ## [[1]]
    ## [1]   2.3   4.0   6.0 -10.0
    ## 
    ## [[2]]
    ## [1] "Hello" "My"    "Name"  "Is"   
    ## 
    ## [[3]]
    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6
    ## 
    ## [[4]]
    ## [1] 22
    ## 
    ## [[5]]
    ## [1] "R is really fun to learn"

### Accessing elements of Vectors, Matrices, and Lists by Index

You access elements of a vector, matrix, or list by enclosing square
brackets around the index number and placing it directly after the
variable name. For example, `x` is a vector with 4 elements in it. To
access the third element execute the following lines:

    x

    ## [1]   2.3   4.0   6.0 -10.0

    x[3]

    ## [1] 6

For matrices you have to specify a row and column index. To get the
element in row 1 column 2,

    z

    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6

    z[1,2]

    ## [1] 3

List elements are accessed similarly.

    list1[3]

    ## [[1]]
    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6

### Data.frame

Data frames in R are conceptually analogous to data you are used to
seeing organized in an excel spreadsheet. Variables are organized by
column and observations are organized by row. The columns can be of
different data types, but rows within one column must be the same. To
illustrate we will use the mtcars data set, which was extracted from the
1974 Motor Trend Magazine and contains fuel consumption and 10 other
variables. The data set is loaded automatically in the standard R
illustration, and it the standard example data set most R tutorials
utilize.

    mtcars

    ##                      mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
    ## Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
    ## AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
    ## Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
    ## Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

We will build our own data frame to build intuition. Suppose we ask 5
people (Peter, Paul, Mary, Simon, and Garfunkel), 3 questions. Height?
Weight? Gender? Columns will represent the variables, and rows will
represent individual answers to those questions. Two new functions
appear in the code snippet below. `cbind()` takes vectors and binds them
together side by side vertically to form columns of a matrix or table.
The function, `data.table()` takes the rectangular object defined by the
`cbind()` function and makes it into a data frame. The argument,
`row.names=` defines the row names as our vector of character strings
containing observation identifiers.

    NAMES    <- c("Peter", "Paul", "Mary", "Simon", "Garfunkel")
    Height   <- c(5.8, 5.5, 5.2, 5.5, 5.6)                                          # I'm making up this data...
    Weight   <- c(150, 155, 120, 145, 160)
    Gender   <- c("Male", "Male", "Female", "Male", "Male")

    DATA     <- data.frame(cbind(Height, Weight, Gender), row.names= NAMES)
    DATA

    ##           Height Weight Gender
    ## Peter        5.8    150   Male
    ## Paul         5.5    155   Male
    ## Mary         5.2    120 Female
    ## Simon        5.5    145   Male
    ## Garfunkel    5.6    160   Male

### Subsetting

There are many ways to slice and dice data frames. We will just
introduce a couple of the most common here. First, if your data frame
has column names you can subset off just one column of the data set by,

    DATA$Weight

    ## [1] 150 155 120 145 160
    ## Levels: 120 145 150 155 160

Alternatively, you can just specify by column number,

    DATA[,2]    # Weight is the second column

    ## [1] 150 155 120 145 160
    ## Levels: 120 145 150 155 160

If we want to only see Mary's stats,

    DATA['Mary',]

    ##      Height Weight Gender
    ## Mary    5.2    120 Female

Or simply specify Mary's row number,

    DATA[3,]

    ##      Height Weight Gender
    ## Mary    5.2    120 Female

Install and Load a Package into the Library
-------------------------------------------

Base R comes with a lot of functionality for statistical analysis, but
the beauty of R lies in the packages contributed by the open source
community. To see what happens if you try to use a function contained in
a package you have not yet installed,

    qplot(DATA$Height)

Anytime you get this error message you know you need to install the
proper package (or you have a typo!). If you simply Google 'R qplot' you
will find the documentation for the function, including the package it
is in. Try it for `qplot`. `...` so you found it is in a package called
`ggplot2`, a powerful package for creating excellent graphics. To
install this package and load it into your library, there are two
methods.

1.  In the lower right pane of RStudio, click the Packages tab, then
    click Install. Now type `ggplot2` and install. Now in the package
    tab, find `ggplot2` in the list of installed packages, click the
    check box. These actions installed `ggplot2` and loaded it into the
    library.

2.  Execute the following code:

<!-- -->
    install.packages("ggplot2")
    library(ggplot2)

Now try the code from above.

    library(ggplot2)
    qplot(DATA$Height)

![](/images/unnamed-chunk-20-1.png)

Now we were able to make a frequency plot for height! It shows how many
observations at each height there are in the data set.

Setting up a Project
--------------------

Initializing an R project is a good way to keep all of your files and
directories straight. It is basically a bundle that saves an image of
your entire R session, and sets the directories to a location you
created it in. If you do not do this, you will inevitably lose track of
what file directory R is pointing to. Then you will save data, figures,
or images in unexpected locations. To get used to working with different
projects, we will create a new project for each chapter of this book.

1.  Click `File`, `New Project`
2.  Choose to save the workspace if prompted.
3.  choose `Existing Directory` since we already created a Chapter1
    folder and saved a script to it.

Now you have an R project for Chapter 1 of this book. Make a new folder
and save an R project to it for each Chapter in the text. We will be
generating file and figures as exercises and arranging R projects this
way will keep us organized.

Other Resources for Getting Started with R
------------------------------------------

This introduction to R is certainly not complete, but it is enough to
get us up and running to start some basic price analysis in the next
chapter. As I noted in the beginning of this chapter, there are so many
free resources for learning R on the web. With the introduction in this
chapter, you are well equipped to explore further if you are interested.
There are a few of links to get you started.

1.  [R for Data Science](http://r4ds.had.co.nz/) by Garrett Grolemund
    and Hadley Wickham

2.  [R Tutorial](http://www.cyclismo.org/tutorial/R/input.html) by Kelly
    Black, Department of Math at University of Georgia.
3.  [R Resources](http://www.ats.ucla.edu/stat/r/) by idre and UCLA.
4.  [Tutorials](http://ww2.coastal.edu/kingw/statistics/R-tutorials/) by
    William King, Coastal Carolina University
5.  [CodeSchool](http://tryr.codeschool.com/levels/1/challenges/1) by
    Code School
6.  [Quick-R](http://www.statmethods.net/) by Robert Kabacoff

And there are so many more. Feel free to find and explore on your own.

Introduction to Data Import
===========================

We will learn how to import data in a variety of ways, including an API
(application program interface) call. Using API's greatly reduce the
work and time required to get up and running with an analysis, and more
entities provide API access all the time.

We will keep the introduction here to the bare minimum required to get
us up and running and performing price analysis.

Data Import From Files on Your Hard Drive
-----------------------------------------

Beginning analysis with R usually involves importing data from our hard
drive. First we will download some data from [Quandl](Quandl.com).

Navigate to where
[CZ2015](https://www.quandl.com/data/CME/CZ2015-Corn-Futures-December-2015-CZ2015)
(December 2015 Corn future) is housed.

![Screenshot of CZ2015 page on Quandl.com](/images/quandlCZ2015.png)

There is a button that says 'download' above the chart of the prices.
When you click it, you will see file format options. We will work with
CSV the most, but will learn how to import Excel files as well. We will
not use json or XML file formats in this book.

### From Comma Separated Files

Let's begin by loading the price data into R in the CSV format. Click
the 'Download' button and then right-click 'CSV'. Choose 'Save Link As'.
This gives you the ability to save it directly into your Chapter1 R
project folder. If you click 'CSV' instead of right-click, the CSV file
will automatically download into your 'Downloads' folder. This is OK,
but you will need to go through the extra step of copy and pasting the
CSV file into your Chapter1 project folder.

Now we have the data on our hard drive, and we will load it into R for
analysis! The `read.csv()` function looks for the file `CME-CZ2015.csv`
in the working directory (file on your hard drive) and loads it into the
R environment as a data.frame. In the "Environment" tab of the upper
right pane of the RStudio console you should see the variable `CZ2015`.
If you hover your mouse over it, RStudio will tell you that it is a
data.frame-type variable and its size.

    CZ2015 <- read.csv(file="CME-CZ2015.csv")

    head(CZ2015)

    ##         Date   Open   High    Low   Last Change Settle Volume
    ## 1 2015-07-27 399.00 399.25 383.00 384.00  19.25 383.50 266575
    ## 2 2015-07-24 413.75 413.75 402.00 402.75  11.00 402.75 135131
    ## 3 2015-07-23 413.75 415.50 408.50 413.25   0.25 413.75 127893
    ## 4 2015-07-22 418.25 418.25 410.25 413.25   4.00 413.50 134747
    ## 5 2015-07-21 417.50 421.00 413.00 417.50   1.50 417.50 141530
    ## 6 2015-07-20 428.00 428.50 415.25 416.50  15.25 416.00 190950
    ##   Open.Interest
    ## 1        568270
    ## 2        568386
    ## 3        574043
    ## 4        572208
    ## 5        571192
    ## 6        557482

    tail(CZ2015)

    ##           Date Open  High Low Last Change Settle Volume Open.Interest
    ## 905 2011-12-21    0   0.0   0   NA     NA 567.75      0             8
    ## 906 2011-12-20    0   0.0   0   NA     NA 562.00      0             8
    ## 907 2011-12-19  555 555.0 555   NA     NA 559.00      1             7
    ## 908 2011-12-16    0   0.0   0   NA     NA 556.50      0             7
    ## 909 2011-12-15  545 549.5 545   NA     NA 550.25      7             0
    ## 910 2011-12-14    0   0.0   0   NA     NA 549.50      0             0

The `head()` function displays the first five rows of data and the
`tail()` displays the last five rows. If you want to see more of the
data you can click on the variable name in the *Environment* tab. You
can see columns for *Date*, *Open*, *High*, *Low*, *Last*, *Change*,
*Settle*, *Volume*, and *Open Interest*. *Open*, loosely defined, is the
price the futures contract was trading at the open of the trading day.
*High* and *Low* are the highest and lowest prices of the day
respectively. *Last* is the price traded at the end of the trading day.
*Settle* is the price determined by the exchange as the price against
which accounts will be settled. This is usually very close to the last
price, but the exchange uses a methodology to arrive at the settle price
based on the price at which the contract was trading in the final
moments of the trading day. If the close was volatile, as it often is,
there can be some difference between the last price and the settle
price. *Change* is the difference between today's *Settle* price and
yesterday's *Settle* price.

### From Microsoft Excel

It is best practice to always download your data as CSV files for the
most flexibility possible. However, R does have the ability to read
Microsoft Excel files, and it works very much like reading in CSV files.
The function we need to do this does not come in the base R package that
gets loaded when you install R. We need to *install* the package "xlsx"
and load it into our *library*. Run the two lines of code below and we
will be ready to use the `read.xlsx()` function from this package to
load our `.xls` data file.

    install.packages("xlsx")
    library(xlsx)

Now that we have the proper package installed, using `read.xlsx()` is
very similar to the `read.csv()` function we used before. The only
addition is that since excel files can have multiple worksheets, we need
to tell the function which worksheet to import. In our case the data
file is simple with only one worksheet, so we just put a 1 in the second
argument of the function.

     CZ2015 <- read.xlsx(file="CME-CZ2015.xls", 1)

Working with API's
------------------

When a website has an API set of for their data warehouse, it is easy to
import data into a programming environment with script. This saves a lot
of time navigating and clicking through websites. Since we are learning
to use R for price analysis, we will definitely want to make use of API
calls when we can. We will need to install another package that provides
functionality to extract information from webpages. Install the `RCurl`
package and load the library by running the following code.

    install.packages("RCurl")
    library(RCurl)

### Quandl's API

In the previous sections we downloaded data from
[Quandl.com](https://quandl.com) manually. They provide an API we can
use to get their data directly into the R environment. To do this we
will make use of the `getURL()` function from the `RCurl` package along
with the `read.csv()` function we used earlier. Run the following code
to download the December 2015 corn futures from
[Quandl.com](https://quandl.com).

    CZ2015 <- getURL("https://www.quandl.com/api/v1/datasets/CME/CZ2015.csv")
    CZ2015 <- read.csv(text = CZ2015)

    head(CZ2015)

    ##         Date   Open   High    Low   Last Change Settle Volume
    ## 1 2015-12-14 373.50 381.75 373.50 381.00   8.75 381.75    903
    ## 2 2015-12-11 377.00 378.75 372.75 373.25   4.25 373.00   2028
    ## 3 2015-12-10 372.50 379.25 371.75 377.00   5.50 377.25   2543
    ## 4 2015-12-09 370.75 376.75 368.50 372.25   1.75 371.75   3217
    ## 5 2015-12-08 369.00 371.00 367.25 370.25   1.50 370.00   2947
    ## 6 2015-12-07 375.75 376.00 368.00 368.25   7.75 368.50   3271
    ##   Open.Interest
    ## 1           816
    ## 2          2474
    ## 3          4444
    ## 4          6411
    ## 5          7935
    ## 6          9503

Note that this is the same data we manually downloaded before. To
download a different data set, you just need to adjust the URL in the
`getURL()` function to point to the right data set. Note the last two
components of the URL, `CME` and `CZ2015.csv` match the "Quandl Code" in
the top right corner of [Quandl.com](https://quandl.com).

For example, if you search on the [Quandl.com](https://quandl.com)
webpage for `CME/SX2015` you can find the November 2015 CME soybeans
futures contract and see that the "Quandl Code" for `SX2015` is
`CME/SX2015`. Now if we adjust our API call above to point to November
2015 soybeans, we will have that data as well.

    SX2015 <- getURL("https://www.quandl.com/api/v1/datasets/CME/SX2015.csv")
    SX2015 <- read.csv(text = SX2015)

    head(SX2015)

    ##         Date   Open   High    Low   Last Change Settle Volume
    ## 1 2015-11-13 871.75 871.75 860.50 860.50  10.25 859.00    110
    ## 2 2015-11-12 869.75 874.75 865.25 869.75   0.75 869.25    925
    ## 3 2015-11-11 865.75 869.75 863.50 868.50   4.00 868.50    763
    ## 4 2015-11-10 875.00 875.25 859.25 866.00   9.00 864.50   1241
    ## 5 2015-11-09 872.00 877.25 871.25 874.00   2.25 873.50   2312
    ## 6 2015-11-06 868.00 873.00 863.25 871.25   3.50 871.25   1327
    ##   Open.Interest
    ## 1            93
    ## 2           978
    ## 3          1997
    ## 4          3313
    ## 5          4324
    ## 6          5260

And now use the API call to get December 2015 soft red winter wheat
futures.

    WZ2015 <- getURL("https://www.quandl.com/api/v1/datasets/CME/WZ2015.csv")
    WZ2015 <- read.csv(text = WZ2015)

    head(WZ2015)

    ##         Date   Open   High    Low   Last Change Settle Volume
    ## 1 2015-12-14 488.00 490.50 488.00 488.75   5.00 487.75     15
    ## 2 2015-12-11 487.50 491.25 480.00 480.50   1.75 482.75     46
    ## 3 2015-12-10 478.50 487.75 476.75 487.75   6.50 484.50     32
    ## 4 2015-12-09 469.75 479.75 469.75 476.00   7.25 478.00     36
    ## 5 2015-12-08 471.00 471.75 466.50 470.25   0.50 470.75    134
    ## 6 2015-12-07 474.75 474.75 471.25 471.25   1.00 470.25    284
    ##   Open.Interest
    ## 1            15
    ## 2            67
    ## 3            86
    ## 4           174
    ## 5           382
    ## 6           346

### USDA API's

Some of the Services within the USDA provide API access to their data
sets. The [USDA Open Data
Catalog](http://www.usda.gov/wps/portal/usda/usdahome?navid=data) is a
collection of all the publicly avaiable USDA datasets. If you click on
the links you will often just go to the web-frontend of a queryable
database. However, there are two links at the top of the webpage that
say 'XML Version' and 'JSON Version'. These links are useful for
accessing the API's that will either allow you to download data directly
into the R environment or reveals the URL that will automatically
download the data in .csv or other useful format that is easily then
imported into the R environment.

<!-- Feedgrains database available here. Historical balance sheet categories-->
<!-- http://www.gipsa.usda.gov/fgis/exportgrain/CY2015.csv  URL format of GIPSA export inspections-->
The URL to use the USDA NASS API for *Corn Ave Prices Received* is not
as simple as the Quandl API above.[1] To use the USDA API's you need to
request and authentication code. This allows the USDA to keep track of
who is accessing the data and make protect against attacks on the data
servers. To request an API, click *obtain an API key* on the
[<http://quickstats.nass.usda.gov/api>](http://quickstats.nass.usda.gov/api).
Then enter the requested information. You will receive an email with the
API key. The code below will download the *Average Prices Recieved by
Farmers* for *Corn* in *Iowa* from *1980* to the present. Of course,
copy and paste your own api key in the link.

    library(RCurl)
    IAPrice <- getURL("https://quickstats.nass.usda.gov/api/api_GET/?key=yourapikey&commodity_desc=CORN&year__GE=1980&state_alpha=IA&format=CSV&statisticcat_desc=PRICE%20RECEIVED")
    IAPrice <- read.csv(text = IAPrice)

    head(IAPrice, 10)

Click on the *Environment* tab in RStudio and click `IAPrice` in the
*Data* section. This will open up the data in RStudio's data viewer.
This is not quite as functional as Microsoft Excel, but it is handy to
verify what you downloaded looks as you expect it to.

Graphing Basics
---------------

The final topic we will cover in this chapter is basic plotting. Above,
we already used `qplot()` from the `ggplot2` package to plot a frequency
chart. The function below, `plot()`, comes installed with base R, so no
need to install any packages before calling the function. We will plot
the corn price data we imported previously in the chapter. It should be
stored as a variable called `CZ2015`. We will plot the *Settle* prices
over time. The `plot()` function takes to arguments. It needs a variable
to plot along the x-axis and a variable to plot along the y-axis. We
will put *Date* along the x-axis and *Settle* prices along the y-axis.

     library(RCurl)
    CZ2015 <- getURL("https://www.quandl.com/api/v1/datasets/CME/CZ2015.csv")

    plot(CZ2015$Dat, CZ2015$Settle)

     library(RCurl)
    CZ2015 <- getURL("https://www.quandl.com/api/v1/datasets/CME/CZ2015.csv")

    plot(CZ2015$Date, CZ2015$Settle)

![](/images/unnamed-chunk-9-1.png)

This plot is OK, but it is not exactly up to par when you think about
what charts in finance, for example, usually look like. The `quantmod`
package has become the most popular R package for charting. Go ahead and
install it an load it into your library.

    install.packages("quantmod")
    install.packages("xts")
    library(quantmod)
    library(xts)

Now, lets plot December 2015 wheat prices that we imported earlier. To
do this we will use the function `chartSeries()` from the `quantmod`
package. It expects data to be a time series, and it expects to receive
Open, High, Low, Close, and Volume.

    library(quantmod)
    WZ2015_chart <- subset(WZ2015, select= -c(Date, Change, Last, Open.Interest))      
    WZ2015_chart <- xts(WZ2015_chart, order.by = as.Date(WZ2015$Date))    
    colnames(WZ2015_chart)[4] <- "Close"    

    chartSeries(WZ2015_chart['2015-01-01/'], type = "candlesticks", theme = chartTheme("white"))

There is a lot going on in this code chunk, actually. Let us go through
the details, but what we just did is pretty advanced so do not feel
overwhelmed. This was mostly to show you what is possible with financial
data. To give you some perspective, it took me about an hour to search
around and get the details right.

The three first lines are all prepping the data to put it into the
format the `chartSeries()` function expects.

1.  In the first line we removed the columns Date, Change, Last,
    Open.Interest because we need only Open, High, Low, Close.
2.  The second line does two things. It defines `WZ2015_chart` as an xts
    time series object, which is just a special class of object in R. It
    has attributes some functions written especially for time series
    data can utilize. The second argument of the `xts()` function uses
    `order.by` to indicate the `WZ2015$Date` variable should be used as
    the date index. and the `as.Date()` function puts the data in a
    proper format the `xts()` function recognizes.
3.  The third line changes the column named "Settle", which is the 4th
    column to "Close". This is because `chartSeries()` wants to see
    columns Open, High, Low, Close, and Volume.

![](/images/unnamed-chunk-12-1.png)

[1] Documentation for the USDA NASS API can be found
<http://quickstats.nass.usda.gov/api>. At this point, do not worry about
understanding how to make sense of the documentation. This is simply a
reference for your possible future use. I will provide all the correct
URLs in the text.

> Be sure to 'Save Workspace Image' when you close the program!
