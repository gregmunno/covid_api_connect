# R Workshop
Nov. 8, 2019, Workshop at the Newhouse School 

## Installing R 
Download and install R at https://cran.case.edu/ (or find your nearest cran at https://cran.r-project.org/ . There maybe one in Puerto Rico)

Download and install RStudio https://www.rstudio.com/products/rstudio/download/ . Not to make sure you install R first, then R Studio 

## What is R?
R is a programing language that specializes in statistical analysis and the plotting of data. Written mostly in C and in R itself, it first appeared in 1993. It is free and open source, and is a top choice for data scientists and academic researchers, and also popular in newsrooms. Developers have created a rich repository of "packages" for R, which create new funtionality and even a different vocabulary for writing code than Base R. These packages have expanded R's usability to include things like data scrapping, textual analysis, and interactive graphics. 

## What is RStudio?
RStudio is an interactive development environment for R. 

## RStudio -- A closer look
In RStudio you generally have four panes -- one to write your scripts (Source), one where your scripts are excuted (Console), one where your data is stored (Environment) and one to navigate to files, visualize data, etc.) You can customize the layout and appearance under "Tools > Global Settings"

Useful keyboard shortcuts can be found at https://support.rstudio.com/hc/en-us/articles/200711853-Keyboard-Shortcuts . Three that get used a lot are:

RUN Code - Ctrl+Enter
Insert PIPE opperator (%) - Ctrl+Shift+M

Insert ASSIGNMENT operator (<-) -	Alt+- (Windows)	Option+- (Mac) 

Clear Console - CTRL+L

At its base, R works like a calculator. So you can type 2+2 in the console and hit return and get 4, or you type 2-2 in scripting pane, click run (or control click), and the result will again appear in the console. 

You can assign values to a variable and then have R priont that value 
```
x <- 2
x 
```
And you can assign a series of values to a variable to create a vector 
```
y <- c(1,2,3,4)
y 
```

# covid_api_connect

```
install.packages("tidyverse")
install.packages("jsonlite")
```

```
library(jsonlite)
library(tidyr)
```

# With PRI data
```
jsondata <- fromJSON("https://covidtrackerapi.bsg.ox.ac.uk/api/v2/stringency/actions/PRI/2020-04-28")
glimpse(jsondata)
df <- as_tibble(jsondata, validate = F)
print(df)
```

# With timeseries (problematic with uneven columns.) 
```
jsondata_tseries <- fromJSON("https://covidtrackerapi.bsg.ox.ac.uk/api/stringency/date-range/2020-01-01/2020-04-26")
glimpse(jsondata_tseries)
df_tseries <- as_tibble(jsondata_tseries, validate = F)
print(df_tseries)
```
