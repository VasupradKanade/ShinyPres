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

## Course Project: [Slidyfy App and Presentation](https://vasupradkanade.github.io/DevelopingDataProducts_W3/UsingPlotly.html)

Coursera Data Science Specialization

<small> [Vasuprad Kanade](https://github.com/VasupradKanade) / [LinkedIn](https://www.linkedin.com/in/vasuprad) </small>

<center>
_"Plot IRIS flower data using ShinyApp and Slidify Presentation"_
</center>


---
# The Assignment 

The goal of this assignment is to build:

1. __A Shiny application__ that has widget input, ui input in `server.R`, reactive output using server calculations, and supporting documentation.

2. __A Reproducible Pitch Presentation__ that contains five slides in either Slidify or Rstudio Presenter that is pushed to and hosted on GitHub or Rpubs and contains embedded `R` code that runs. 

### Links to Project App & Docs

1. Shiny App: [Link](https://vasupradkanade.shinyapps.io/ShinyAppIris/)

2. `server.R` and `ui.R` files: [Link](https://github.com/VasupradKanade/ShinyApp) 

---
# The Data

The Iris flower data set or Fisher's Iris data set is a multivariate data set introduced by the British statistician and biologist *Ronald Fisher* in his 1936 paper The use of multiple measurements in taxonomic problems as an example of linear discriminant analysis


The data set consists of 50 samples from each of three species of *__Iris__ (Iris setosa, Iris virginica and Iris versicolor)*. Four features were measured from each sample: the length and the width of the sepals and petals, in centimetres. Based on the combination of these four features, Fisher developed a linear discriminant model to distinguish the species from each other.

---
# Code Example
#### Plot IRIS flower data using Plotly
This segment of code selects the relevant data columns, aggregates the three speciees of Iris flower by petal and sepal length.

```r
filename <- "iris.csv"

# Load the CSV file from the local directory
dataset <- read.csv(filename, header=FALSE)

# Set the column names in the dataset
colnames(dataset) <- c("Sepal.Length","Sepal.Width","Petal.Length","Petal.Width","Species")
```

---
# Plot using Plotly
Using ColorBrewer Palette Names


<pre><iframe src="./assets/img/plot1.html" width=750px height=400px allowtransparency="true" scrolling="no" seamless="seamless" frameBorder="0"> </iframe></pre>

