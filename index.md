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
  folium-chart-1: ["charts/folium_choropleth_community_crimes.html", "600"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
  px-chart-1: ["charts/chart_crime_count.html", "500"]
  px-chart-2: ["charts/chart_crime_location.html", "400"]
  px-chart-3: ["charts/chart_crimes_community.html", "950"]
  px-chart-4: ["charts/chart_histogram_of_crimes_by_month.html", "300"]
  px-chart-5: ["charts/chart_domestic_violence_rate.html", "400"]
  px-chart-6: ["charts/chart_crime_arrest_rate.html", "400"]
  png-1: ["assets/img/density_of_different_crimes.png",700]
  png-2: ["assets/img/spatial_cluster_analysis.png",500]
  png-3: ["assets/img/hexgrids_nn.png",800]
  
 
---

# Introduction

Chicago is a city steeped in rich history and cultural heritage. Unfortunately, it is also plagued by crime. Ensuring the safety of its citizens is a persistent challenge that law enforcement agencies are continually trying to tackle.

Social safety is a constant problem that affects the lives of its citizens. Understanding crime, predicting it, and preventing it have become something that police departments want to do. As in the movie Minority Report, a "prophet" predicts crimes before they happen. Nevertheless, reality is not a science fiction movie, and crime prediction is a complex problem because many random human factors are involved. The specifics of how crime is committed vary depending on the type of society and community.

In 2022, Victor Rotaru, Yi Huang, Timmy Li, James Evans, and Ishanu Chattopadhyay developed a new algorithm to predict urban crime at the individual event level a week or more in advance, enabling model-based simulations that reveal both the pattern of reported infractions and the pattern of corresponding police enforcement. Meanwhile, in 2021, Suhong Kim, Param Joshi, Parminder Singh Kalsi, and Pooya Taheri et al. implemented a machine learning prediction model to predict crime in Vancouver.

Like the above studies, in this exercise, I attempted to use machine learning to predict crime rates in Chicago by analyzing data from previous crimes records. The prediction model also includes social factors that may affect crime rates. The overall crime rate of a city is calculated by dividing the total number of crimes submitted by police agencies in the city by the city's population and multiplying the result by 100,000.

The project is broken down into five parts:
1. `Data wrangling`: This involves cleaning, joining, merging, and transforming the crime dataset.
2. `Exploratory Analysis`: In this section, the crime trend will be analyzed from a community-based perspective, taking into account the type of crime, location, time series, arrest rate, and domestic violence rate.
3. `Feature Engineering`: This involves analyzing the spatial patterns of crime, examining the `density` of different types of crimes, `clustering` crime events, using `KNN algorithms` to capture similarities, and classifying the distance between crime sites and nearby feature points.
4. `Predictive Modeling` of Crime Count: This section focuses on predicting the crime rate of the city.
5. `Evaluation`: In this final stage, the performance of the model will be evaluated and errors will be validated.

---

# What Exactly Exists
The raw data used in this project consists of crime records from 2015 to 2019 obtained from the Chicago Data Portal. With a total of 1303648 records, the dataset provides detailed information on the primary type of crime, the crime's description, its location, and other relevant police information, such as community, time, district, and more.

The second dataset used in this project is the Chicago neighborhood dataset, which contains the names, numbers, and geographic boundaries of 77 communities. To make use of this data, it was preprocessed by reading the JSON files from the API and merging them using the `concat` function. The formatting was then adjusted for date and time, numeric variables, and categorical variables. Additionally, relevant features were added to the dataset using the `merge` function, including community information and socioeconomic information. Finally, several indices were calculated, such as the crime count by community, weapon count, month count, week count, arrest index, and domestic index.

The dataset was grouped by communities and sorted to create a new dataset of crime events for each community. An interactive choropleth map was created using the `folium` function, displaying the cumulative crime events over 5 years for each community. The map reveals that crime events are generally concentrated in a few communities in the city, particularly on the south side.

<div id="folium-chart-1"></div>


---

# Community-based Perspective

### Plotly Charts

Additionally, the charts provide insight into the most common location and time of occurrence for each type of crime. For example, it appears that theft is most commonly recorded at street locations, while battery and assault are most commonly recorded at residential locations. The charts also show the trend of crime occurrence over time, indicating that crime rates may vary depending on the season and month of the year.

In terms of district, it can be seen that some districts have higher crime rates compared to others. For example, some districts may have a higher rate of theft, while others may have a higher rate of battery. By examining the distribution of crime events across the different districts, police departments can allocate resources more effectively to areas with higher crime rates.

`Plotly.express` and `altair` packages have been used here to create corresponding interactive charts. These charts show that theft, battery, criminal damage, assault, other offense, deceptive practice, narcotics, burglary, motor vehicle theft, and robbery topped the list of crimes with criminal records. 

<div id="px-chart-1"></div>

The data visualization also provides insight into the relationship between crime and location. Crime rates were similar indoors and outdoors. Streets were the most frequent areas, followed by residences and apartments.
<div id="px-chart-2"></div>

Comparing the different types of crime in different communities shows the distribution and frequency of crime incidents in each community. It can be seen that theft, battery, robbery, and narcotics are widely distributed in each community. 
<div id="px-chart-3"></div>

Furthermore, the time series allows us to know the trend of crime occurrence. As can be seen from the following plot, crime is not a cumulative or increasing-decreasing phenomenon. It is a continuous, cyclical, extensive, and random process. 

From this, we can see a regular correlation between crime occurrence and months, with May to October having a higher frequency than other months, especially in the summer months (July and August) as the period with high incidences of cases. It shows that the weather (temperature, precipitation, cold) is also a critical factor in crime incidents. This could be because people tend to be out more and socializing during these time, which can create opportunities for criminal activities.
<div id="px-chart-4"></div>

Some crimes have a 100% arrest rate, and we should be concerned about which crimes have lower arrest rates, such as burglary, kidnapping, robbery, criminal sexual assault, and theft, which can become hidden dangers.
<div id="px-chart-5"></div>

<div id="px-chart-6"></div>


### Heatmap

A total of 31 Chicago districts are represented in this dataset. Based on the districts heatmap, we can identify the number of specific types of crimes that have occurred in various districts in the last five years. The darker the color, the lower the number of crimes, which shows that some crimes, such as assault, burglary, motor vehicle theft, narcotics, theft, and criminal damage, have a high frequency in all districts. 

In contrast, obscenity, stalking, kidnapping, intimidation, human trafficking, criminal sexual assault, etc., occur less frequently. Aditionnally, some crimes are concentrated in specific areas, such as prostitution in district 7 and district 11.
<div id="heatmap-1"></div>

However, when it comes to community security, some communities have been experiencing policing problems for these five years. In the community heatmap, we know that these communities, such as Austin, Auburn Gresham, Loop, Near North Side, Near West Side, North Lawndale, Roseland, South Shore, West Englewood, and West Town, all have a high crime rate. These communities may have some security problems.
<div id="heatmap-2"></div>

Similarly, the day of the week heatmap allows us to understand the crime trend over the week. The chart shows that crimes are more likely to occur in the daytime, such as offenses involving children. some crimes are more likely to occur in the night, especially criminal sexual assault. This information is valuable for both the police and the community, as they can prepare accordingly.
<div id="heatmap-3"></div>

In conclusion, the exploratory analysis provides valuable insights into the nature of crime in Chicago. By visualizing the crime data, it becomes easier to identify patterns, trends, and relationships between different variables. This information can help police departments make data-driven decisions for crime prevention and reduction efforts.

---
# Crime Spatial Patterns

Different types of crime are being distributed unevenly across the complex landscape of modern cities. KDEs are a popular tool for analyzing data distributions. In the kernel density estimate, 9 representative types such as ROBBERY, THEFT, BURGLARY, WEAPONS VIOLATION, NARCOTICS, ASSAULT, HOMICIDE, SEX OFFENSE, and KIDNAPPING are displayed. 

It is worth mentioning that the KDE gives an unequivocal demonstration of the spatial distribution. We can see that while theft occurs widely throughout the city, it is most concentrated in downtown areas, while narcotics are concentrated in the area on the west side of downtown. For the rest of the several crimes, different peaks can be seen scattered in several city areas.

<div id="png-1"></div>

The `KNN` analysis helps us understand the relationship between crime and amenities. It is used to calculate the log-transformed distance between crime locations and amenity locations. This information can be used to identify areas with high or low levels of access to amenities, which can impact crime patterns. For example, areas with higher levels of access to amenities such as shops, schools, and community centers, may have lower crime rates, while areas with low levels of access may have higher crime rates. By analyzing the distance between crime locations and amenity locations, we can determine which types of amenities are more related to the crime and what factors contribute to the crime.

The result is that cluster-0 includes 31 communities with an average crime incident of 10043, cluster-1 includes 17 communities with an average crime incident of 30559, cluster-2 includes 5 communities with an average crime incident of 42966, cluster-3 includes 1 community with an average crime incident of 77134, cluster-4 includes 23 communities with an average crime incident of 7862. Last but not least, the hexagonal grid map shows the clusters in more detailly. Using the h3fy function from the tobler.util module can easily generate a hexgrids covering the face of the Chicago City.

<div id="png-2"></div>

Some features would help predict the crime rate, such as the proximity to depository places, bars, pubs, and liquor retailers, and the location near commercials place, universities, schools, landmarks, shot spotter alerts, or subway stations. Moreover, the crime probably happened in abandoned buildings and vehicles in some areas. Likewise, some socioeconomic features, such as the economic hardship index, can be critical factors in community development and security issues. Specifically, there are some factors related to the
number of crimes:

1. Depository locations
2. Abandon buildings
3. Schools
4. Grocery stores
5. Subway stations
6. Retails and commercials
7. Landmarks
8. ShotSpotter alerts

In addition, the sklearn.neighbors.NearestNeighbors provides a regression for data with continuous labels. It identifies the nearest neighbors of a given query point, and the commonly used distance metric is the Euclidean distance. In this project, the nearest neighbors places of crime occurrence are found. The value of k varies according to different places, for instance, 5 nearest depository locations, 5 nearest abandoned buildings, 3 nearest schools, 3 nearest grocery stores, 5 nearest subway stations, 5 nearest shopping areas, 2 nearest landmarks, and 3 nearest shot spotter alerts. The darker the color, the farther the distance. These maps show that depository locations and subway stations are concentrated in the city, and abandoned buildings are concentrated on the city's west side and some areas in the middle of the city. Schools are located throughout the city, while grocery stores, retail, and commercials are concentrated in some neighborhoods.

<div id="png-3"></div>

---
# A New Predictive Try

---
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
