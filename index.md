---
layout: default
altair-loader:
  altair-chart-1: "charts/measlesAltair.json"
  heatmap-1: "charts/heatmap_district.json"
  heatmap-2: "charts/heatmap_time.json"
  heatmap-3: "charts/heatmap_hour.json"
hv-loader:
  hv-chart-1: ["charts/measlesHvplot.html", "500"] # second argument is the desired height
folium-loader:
  folium-chart-1: ["charts/folium_choropleth_community_crimes.html", "700"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
  px-chart-1: ["charts/chart_crime_count.html", "500"]
  px-chart-2: ["charts/chart_crime_location.html", "400"]
  px-chart-3: ["charts/chart_crimes_community.html", "850"]
  px-chart-4: ["charts/chart_histogram_of_crimes_by_month.html", "400"]
  

toc: true 
read_time: true
toc_sticky: true
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


# What Exactly Exists
The raw data is crime records from 2015 to 2019 from Chicago Data Portal. Due to the dataset missing some factors after 2019, I choose data from these 5 years. Thus the dataset has a total of 1303648 records and contains descriptive information on the primary type of crime, description of the crime, location description of the crime, and the community, time, district, and other police information.

The second dataset is the Chicago neighborhood dataset, which includes the names, numbers, and geographic boundaries of 77 communities. Based on the dataset, I preprocessed the data using the read_json read files from API and merged them using the concat function. Next, the formatting was done to adjust the formatting for date and time, numeric variables, and categorical variables. Afterward, relevant features were added to the dataset using merge, including community information and socioeconomic information. Finally, crime count by the community, weapon count, month count, week count, arrest index, and domestic index were calculated.

Based on the dataset above, this section is designed to show the basic crime trending in Chicago.


### Folium Choropleth Map
<div id="folium-chart-1"></div>

First, the dataset is grouped by communities and sorted to obtain a new dataset of crime events for each community. I use the `folium` function to create an interactive choropleth map showing the community's cumulative crime events over 5 years. As shown in the graph, crime events are generally concentrated in several communities in the city and several communities around the south side.


# Community-based Perspective

### Ploty Interactive Charts

This data set is sorted according to the type of crime, the location, the district number, and the month the crime occurred. 

`Plotly.express` and `altair` packages have been used here to create corresponding interactive charts. These charts show that theft, battery, criminal damage, assault, other offense, deceptive practice, narcotics, burglary, motor vehicle theft, and robbery topped the list of crimes with criminal records. 

> Crime Count
<div id="px-chart-1"></div>

> Crime Location
Crime rates were similar indoors and outdoors. Streets were the most frequent areas, followed by residences and apartments.
<div id="px-chart-2"></div>

> Community
Comparing the different types of crime in different communities shows the distribution and frequency of crime incidents in each community. It can be seen that theft, battery, robbery, and narcotics are widely distributed in each community.
<div id="px-chart-3"></div>

> Time Series
Furthermore, the time series allows us to know the trend of crime occurrence. As can be seen from the following plot, crime is not a cumulative or increasing-decreasing phenomenon. It is a continuous, cyclical, extensive, and random process. 
<div id="px-chart-4"></div>
From this, we can see a regular correlation between crime occurrence and months, with May to October having a higher frequency than other months, especially in the summer months (July and August) as the period with high incidences of cases. It shows that the weather (temperature, precipitation, cold) is also a critical factor in crime incidents.

### Heatmap
> District Heatmap
A total of 31 Chicago districts are represented in this dataset. Based on the districts heatmap, we can identify the number of specific types of crimes that have occurred in various districts in the last five years. The darker the color, the lower the number of crimes, which shows that some crimes, such as assault, burglary, motor vehicle theft, narcotics, theft, and criminal damage, have a high frequency in all districts. 
<div id="heatmap-1"></div>
In contrast, obscenity, stalking, kidnapping, intimidation, human trafficking, criminal sexual assault, etc., occur less frequently. Aditionnally, some crimes are concentrated in specific areas, such as prostitution in district 7 and district 11.

> Community Heatmap
However, when it comes to community security, some communities have been experiencing policing problems for these five years. In the community heatmap, we know that these communities, such as Austin, Auburn Gresham, Loop, Near North Side, Near West Side, North Lawndale, Roseland, South Shore, West Englewood, and West Town, all have a high crime rate. These communities may have some security problems.
- Community Heatmap - By Month
<div id="heatmap-2"></div>

> Time Heatmap
In the hour heatmap, we know that among the 24 hours a day, some crimes are concentrated in the daytime, such as offenses involving children, some crimes are concentrated in the night, such as criminal sexual assault, and some are high in frequency 24 hours a day.
- Hour Heatmap - By Hour
<div id="heatmap-3"></div>

# Crime Spatial Patterns

# A New Predictive Try

# Examine Errors


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
