---
title       : Developing Data Products - Shiny Application and Presentation
subtitle    : Course 9 - Week 4 - Assignment Presentation
author      : Vasuprad Kanade
job         : Coursera Data Science Specialization
framework   : revealjs        # {io2012, html5slides, shower, dzslides, ...}
revealjs    : {theme: moon, transition: convex}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : zenburn
widgets     : [bootstrap]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---


# Developing Data Products
---------------------

## Course Project: [Plot using Plotly](https://vasupradkanade.github.io/DevelopingDataProducts_W3/UsingPlotly.html)

Coursera Data Science Specialization

<small> [Vasuprad Kanade](github.com/VasupradKanade) / [LinkedIn](https://www.linkedin.com/in/vasuprad) </small>

<center>
_"Turn sales information into insight through the magic of Shiny"_
</center>


---
## The Assignment 

The goal of this assignment is to build:

1. __A Shiny application__ that has widget input, ui input in `server.R`, reactive output using server calculations, and supporting documentation.

2. __A Reproducible Pitch Presentation__ that contains five slides in either Slidify or Rstudio Presenter that is pushed to and hosted on GitHub or Rpubs and contains embedded `R` code that runs. 

### Links to Project App & Docs

1. Shiny App: [Link](https://vasupradkanade.shinyapps.io/Wk4ShinyApp/)

2. `server.R` and `ui.R` files: [Link](https://github.com/VasupradKanade/ShinyApp) 

---  
## The Sales Analytics Dashboard

#### Make Selections to Unlock Insights

There's a lot you can do with the __Sales Analytics Dashboard__. Here's a few suggestion to get started:

* Imagine you are an executive at _Cannondale_ in charge of strategy and business development. Your goal is to understand which products _Cannondale's_ customers are purchasing, which customers are purchasing the most, and what the organization can do to improve sales.

* Use the __Reactive Inputs__ to filter by year, product unit price, product primary category, and product secondary category. 

* On the __Analysis__ tab, see how the filters can be used to drill into the information. See if there are any insights that you can come up with from the data.

* Switch to the __Data__ tab to see how the filters control the data. Subset the data, and try downloading the csv file. 

* Use the __Reset Fields__ button when finished. See how the data set refreshs to its original size and how all of the reactive inputs reset.

--- 
## Code Example

#### Leaflet: Visualize Customers By Location



```r
library(leaflet)
library(htmlwidgets)
library(knitr)
library(dplyr)

# Load data
source("helper.R")
orders.extended <- read.data()

# Get sales by location
salesByLocation <- orders.extended %>%
        group_by(bikeshop.name, longitude, latitude) %>%
        summarise(total.sales = sum(price.extended)) %>%
        mutate(popup = paste0(bikeshop.name, 
                              ": ", 
                              scales::dollar(total.sales)))

# Use Leaflet package to create map visualizing sales by customer location
l <- leaflet(salesByLocation) %>% 
  addProviderTiles("CartoDB.Positron") %>%
  addMarkers(lng = ~longitude, 
             lat = ~latitude,
             popup = ~popup) %>%
  addCircles(lng = ~longitude, 
             lat = ~latitude, 
             weight = 2,
             radius = ~(total.sales)^0.775)

# Move to img folder
setwd("./assets/img")
saveWidget(l, 'leaflet1.html') # Save widget html
setwd("../..")

# Source saved file
cat('<pre><iframe src="./assets/img/leaflet1.html" width=100% height=350px allowtransparency="true"> </iframe></pre>')
```

<pre><iframe src="./assets/img/leaflet1.html" width=100% height=350px allowtransparency="true"> </iframe></pre>
