---
layout: default
altair-loader:
  altair-chart-1: "charts/measlesAltair.json"
hv-loader:
  hv-chart-1: ["charts/measlesHvplot.html", "500"] # second argument is the desired height
folium-loader:
  folium-chart-1: ["charts/foliumChart.html", "400"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
---

# Introduction

Chicago is a city with rich history and cultural heritage. However, the city is also encroached upon by crime. 

Social security is a constant problem that affects the lives of its citizens. Understanding crime, predicting it, and preventing it have become something that police departments want to do. As in the movie Minority Report, a "prophet" predicts crimes before they happen. Nevertheless, reality is not a science fiction movie, and Crime prediction is a complex problem because many random human factors are involved. The specifics of how crime is committed vary depending on the type of society and community.

In 2022, Victor Rotaru, Yi Huang, Timmy Li, James Evans, and Ishanu Chattopadhyay developed a new algorithm to predict urban crime at the individual event level a week or more in advance, enabling model-based simulations that reveal both the pattern of reported infractions and the pattern of corresponding police enforcement. Meanwhile, in 2021, Suhong Kim, Param Joshi, Parminder Singh Kalsi, and Pooya Taheri et al. implemented a machine learning prediction model to predict crime in Vancouver.

Like the above studies, in this exercise, I attempted to use machine learning to predict crime rates in Chicago by analyzing data from previous crimes records. The prediction model also includes social factors that may affect crime rates. The overall crime rate of a city is calculated by dividing the total number of crimes submitted by police agencies in the city by the city's population and multiplying the result by 100,000.

This project is divided into five parts.
- **Part 1** - `Data wrangling`: clean, join, merge, and transform the crime dataset
- **Part 2** - `Exploratory Analysis`: check out the crime trending with a community-based perspective on crime type, location, time series, arrest rate, and domestic violence rate
- **Part 3** - `Feature Engineering`: examine the spatial patterns of crime, analyze the density of different types of crimes, analyze the `clustering` of crime events, use `KNN algorithm` to capture the similarity, and classify the distance between crime sites to and nearby feature points
- **Part 4** - Predictive Modeling of Crime Count: predict the crime rate of the city 
- **Part 5** - Evaluation: validate errors and examine the performance of the model


## Part 1 - What exactly exists

## Part 2 - Community-based perspective


Here are some packages used in this project, click [this page](./another-page.html) to check out.

# Example: Embedding Altair & Hvplot Charts

This section will show examples of embedding interactive charts produced using [Altair](https://altair-viz.github.io) and [Hvplot](https://hvplot.pyviz.org/).

## Altair Example

Below is a chart of the incidence of measles since 1928 for the 50 US states.

<div id="altair-chart-1"></div>

This was produced using Altair and embedded in this static web page. Note that you can also display Python code on this page:

```python
import altair as alt
alt.renderers.enable('notebook')
```

## HvPlot Example

Lastly, the measles incidence produced using the HvPlot package:

<div id="hv-chart-1"></div>

## Notes

- See the [lecture 13A slides](https://musa-550-fall-2022.github.io/slideslecture-13A.html) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**

# Example: Embedding Folium charts

This post will show examples of embedding interactive maps produced using [Folium](https://github.com/python-visualization/folium).

## OSMnx and Street Networks

The shortest route between the Art Museum and the Liberty Bell:

<div id="folium-chart-1"></div>

<br/>

## Percentage of Households without Internet

The percentage of households without internet by county:

<div id="folium-chart-2"></div>

See the [lecture 9B slides](https://musa-550-fall-2022.github.io/slides/lecture-9B.html) and the [lecture 10A slides](https://musa-550-fall-2022.github.io/slides/lecture-10A.html) for the code that produced these plots.
