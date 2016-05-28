---
title       : Altman Z-score Calculator
subtitle    : Developing Data Products__Course Project
author      : George Kolev
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---


## Introduction

The <b>Altman Z-score</b> formula is widely used for assessing the health of a public company and predicting the likelihood of financial distress or bankruptcy within 2 years, using data from the company's balance sheet and income statement.

For the Coursera Data Products Course Project, I developed a Shiny app, which automates the calculation of a company's Z-score.

The Shiny app is located at:<br>
https://gikolev.shinyapps.io/Altman_Z-score_Calculator/

The source code is located at:<br>
https://github.com/gikolev/data_products_project

--- .class #id bg:#FFFFFF

## Using the Application

The app requires the input of several financial metrics, and uses them to calculate and interpret the company's Z-score.

The <b>Sample Data</b> tab contains financial parameters for two companies - Apple and Chesapeake Energy Corp. - which can be used to test the Shiny app's functionality and compare the companies' Z-scores.

Sources for confirming financial metrics include: Yahoo! Finance, Morningstar, and a company's published annual reports.


--- .class #id bg:#FFFFFF

## Derivation

The following parameters are provided (using Apple's data as an example): 

```r
WC <- 8768 ## Working Capital
TA <- 290479 ## Total Assets
RE <- 92284 ## Retained Earnings
EBIT <- 72515 ## Earnings before Interest and Taxes
MVE <- 554000 ## Market Value of Equity
TL <- 171124 ## Book Value of Total Liabilities
S <- 233715 ## Sales
```

The Z-score is a linear combination of five key ratios, weighted by coefficients:

```r
Z <- round(1.2*(WC/TA) + 1.4*(RE/TA) + 3.3*(EBIT/TA) + 0.6*(MVE/TL)+ 1.0*(S/TA), 2)
print(Z)
```

```
## [1] 4.05
```

--- .class #id bg:#FFFFFF

## Interpreting the Z-score

The level of financial distress is estimated, based on the range or 'zone' the score falls into: 

<b>Z > 2.99 - Safe Zone. </b> <br>
The company is in good financial health and not likely to experience distress or to go bankrupt within the next two years. 

<b>1.81 < Z < 2.99 - Grey Zone.</b> </br>
The score is inconclusive, so caution is warranted. 

<b>Z < 1.81 - Distress Zone.</b> </br>
There is a high probability of financial distress or bankruptcy within the next two years.

Unsurprisingly, Apple's Z-score at the end of 2015 indicates that it is in good financial health.
