# INTRODUCTION - Chicago Crime Rate Prediction

This is my final project for MUSA 550(Geospatial Data Science in Python). In this project, I am trying to build a predictive model based on the previous crime records in Chicago. Click this [link](https://cyber-hbliu.github.io/Crime-Prediction-In-Chicago/) to know more details about the project.

## Background
Chicago is a city with rich history and cultural heritage. However, the city is also encroached upon by crime. Social security is a constant problem that affects the lives of its citizens. Understanding crime, predicting it, and preventing it have become something that police departments want to do. As in the movie Minority Report, a "prophet" predicts crimes before they happen. Nevertheless, reality is not a science fiction movie, and Crime prediction is a complex problem because many random human factors are involved. The specifics of how crime is committed vary depending on the type of society and community.

In 2022, Victor Rotaru, Yi Huang, Timmy Li, James Evans, and Ishanu Chattopadhyay developed a new algorithm to predict urban crime at the individual event level a week or more in advance, enabling model-based simulations that reveal both the pattern of reported infractions and the pattern of corresponding police enforcement. Meanwhile, in 2021, Suhong Kim, Param Joshi, Parminder Singh Kalsi, and Pooya Taheri et al. implemented a machine learning prediction model to predict crime in Vancouver.

Like the above studies, in this exercise, I attempted to use machine learning to predict crime rates in Chicago by analyzing data from previous crimes records. The prediction model also includes social factors that may affect crime rates. The overall crime rate of a city is calculated by dividing the total number of crimes submitted by police agencies in the city by the city's population and multiplying the result by 100,000.

## Structure
This project is divided into five parts.

- Part 1 - Data wrangling: clean, join, merge, and transform the crime dataset
- Part 2 - Exploratory Analysis: check out the crime trending with a community-based perspective on crime type, location, time series, arrest rate, and domestic violence rate
- Part 3 - Feature Engineering: examine the spatial patterns of crime, analyze the density of different types of crimes, analyze the clustering of crime events, use KNN algorithm to capture the similarity, and classify the distance between crime sites to and nearby feature points
- Part 4 - Predictive Modeling of Crime Count: predict the crime rate of the city 
- Part 5 - Evaluation: validate errors and examine the performance of the model

