---
layout: post
title: "Weather Forecast Web App"
date: 2022-11-01
categories: projects
featured_image: weatherApp.jpeg
excerpt_separator: <!--more-->
---

For an upcoming project I'm interested in building (a custom magic mirror) I wanted to familiarize myself with [OpenWeatherMap's](https://openweathermap.org) forecasting APIs and continue to work on my Javascript / CSS skills. So I decided to build a simple desktop web-app capable of searching for locations and displaying the corresponding weather data. This project leveraged two of OpenWeatherMap's APIs available for free trials. The first was the Geocoding [API](https://openweathermap.org/api/geocoding-api), which I used to convert user entered locations into Latitude and Longitude coordinates. With the coordinates in hand, it is then a simple exercise to retrieve the current and forecasted weather conditions with the One Call [API](https://openweathermap.org/api/one-call-3). 

The repository for this project can be found [here](https://github.com/connor-passe/weather-app), and the live site [here](https://connorpasse.com/weather-app/).

![](/assets/images/weatherApp.jpeg)


