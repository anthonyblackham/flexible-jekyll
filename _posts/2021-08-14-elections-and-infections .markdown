---
layout: post
title: Elections and Infections
date: 2021-08-14 5:30:00 -0800
description: Using D3 to visualize data # Add post description (optional)
img: elections-cover.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [d3, election]
---

There is no shortage of data and tools available to manipulate data. I've primarily used leaflet and qgis to work on web maps but thought it would be a fun exercise to try out some data visualization using [D3.js](https://d3js.org/)

If you remember the post on [Cartograms](https://anthonyblackham.com/cartograms/) this may look familiar. I wanted to see how the vaccination rates for Covid-19 compared to the election results by state. I pulled some data from the CDC as of August 13 2021 for the percent of people fully vaccinated. I pulled data from the FEC to show which candidate had the majority in each state. 

Here is a graphic showing the 2020 election results by candidate:

<div class="embed-container">
  <iframe
      src="https://anthonyblackham.com/elections-infections/election/"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

Here is a dorling cartogram scaling each state based on the percentage of the population vaccinated as of August 13 2021.

<div class="embed-container">
  <iframe
      src="https://anthonyblackham.com/elections-infections/dorling/"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

I may look into a [non-contiguous cartogram](https://observablehq.com/@d3/non-contiguous-cartogram) and/or a [bivariate choropleth](https://observablehq.com/@d3/bivariate-choropleth) for a few more examples of how the data can be manipulated but for now these will be sufficient. 

### Covid-19 Vaccinations

The colored area of each state represents the proportion of the state’s fully vaccinated population. Data: [CDC](https://data.cdc.gov/Vaccinations/COVID-19-Vaccinations-in-the-United-States-Jurisdi/unsk-b7fc)`

<iframe width="100%" height="713" frameborder="0"
  src="https://observablehq.com/embed/@herbfargus/covid-19-vaccinations?cells=viewof+year%2Cchart"></iframe>

I'll let the data speak for itself but [this](https://www.nytimes.com/interactive/2021/04/17/us/vaccine-hesitancy-politics.html) is an interesting article by the New York Times that goes more into depth on the relationship between vaccinations and political affiliation. 
