---
layout: post
title: Elections and Infections
date: 2021-08-14 5:30:00 -0800
description: Using D3 to visualize data # Add post description (optional)
img: elections-cover.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [d3, election]
---

I wanted to see how the vaccination rates for Covid-19 compared to the election results by state. I pulled some data from the CDC as of August 13 2021 for the percent of people fully vaccinated. I pulled data from the FEC to show which candidate had the majority in each state. If you remember the post on [Cartograms](https://anthonyblackham.com/cartograms/) this may look familiar.  

There is no shortage of ways to manipulate and visualize data. While my primary work is in traditional GIS desktop software, there are many different tools suited for platforms outside of the typical work enviroment. [D3.js](https://d3js.org/) is a javascript library specifically geared toward data visualisation. It has some pretty useful tools on its own but it's also flexible enough to be used with libraries like Leaflet. 

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

### Dorling

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

Here is a non-contiguous cartogram from [ObservableHQ](https://observablehq.com/) that shows various vaccination rates from 2021. 

<iframe width="100%" height="500" frameborder="0"
  src="https://observablehq.com/embed/@herbfargus/covid-19-vaccinations?cell=*"></iframe>

I also included some tradition exhibits generated in QGIS:

### Non-Contiguous

![Non-Contiguous Cartogram]({{site.baseurl}}/assets/img/vaccine-non-contiguous.png)

### Hexagon

![Hexagon Cartogram]({{site.baseurl}}/assets/img/vaccine-hex.png)

### Grid

![Grid Cartogram]({{site.baseurl}}/assets/img/vaccine-grid.png)

A [bivariate choropleth](https://observablehq.com/@d3/bivariate-choropleth) might be another good graphic to try in the future.

I'll let the data speak for itself but [this](https://www.nytimes.com/interactive/2021/04/17/us/vaccine-hesitancy-politics.html) is an interesting article by the New York Times that goes more into depth on the relationship between vaccinations and political affiliation. 
