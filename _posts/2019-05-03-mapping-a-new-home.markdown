---
layout: post
title: Mapping a New Home
date: 2020-05-03 5:30:00 -0800
description: Making a hazard and landscaping map for a new home(optional)
img: home-cover.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [as-built, landscape, QGIS, hazard, earthquake]
---

My friend was in the market for a new home and knowing my background with geology asked me where a suitable place was to build in the Wasatch Valley. I got to work on gathering sources and data to come up with a map that I could share with them to show the potential geologic hazards around some potential home sites.

### Hazard Map:

A few options were by Utah Lake which is along the Wasatch Fault sytem. Low water tables mixed with seismic activity means liquefaction can be a real possibility. The Utah Geological Survey hosts various hazard maps and resultant GIS data sets that can be used. The geologic data sets come with a disclaimer of accuracy since many of the current GIS data sets are digitzed from older geologic studies.

Utah County Liquefaction Potential Publication:

[https://ugspub.nr.utah.gov/publications/public_information/pi-28.pdf](https://ugspub.nr.utah.gov/publications/public_information/pi-28.pdf)

![Utah County Liquefaction Map]({{site.baseurl}}/assets/img/home-liquefaction.png)

GIS Data Portal:

[https://opendata.gis.utah.gov/datasets/utah-liquefaction-potential](https://opendata.gis.utah.gov/datasets/utah-liquefaction-potential)

Once I acquired the liqeufaction data I also needed to acquire the historic and recent earthquake data which the United States Geological Survey (USGS) provides.

[https://earthquake.usgs.gov/earthquakes/map/](https://earthquake.usgs.gov/earthquakes/map/)

I pulled all the data together in QGIS and symbolized it accordingly and this was the end result:

![Home Hazard Map]({{site.baseurl}}/assets/img/home-hazard.png)

### Landscape Map

A few months later my friend found a suitable location they were happy with and knowing my backround with my landscaping work at my university, they showed me their hand drawn landscaping plans. It was a nice sketch but for their new home I thought they should have something a bit more tailored so I got to work on drafting up a map.

First I pulled their deed and original plat map for their development to make sure that what they measured out reflected the legal boundaries of their property.

![Home Plat]({{site.baseurl}}/assets/img/home-plat.png)

Once I verified the measurements were correct I opened up QGIS and pulled in some updated aerial imagery from Google and overlaid the county parcel data that reflected the recorded plat. Then it was just a matter of recreating the hand drawn sketch.
 
This was the final result:
 
![Home Plat]({{site.baseurl}}/assets/img/home-landscape.png)

### Future

I would like to revisit this in a few years once the plants have grown and the satellite imagery of the area has been updated to see how closely what I drew reflected what ended up being developed.
