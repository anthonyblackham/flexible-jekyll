---
layout: post
title: Oregon Fires
date: 2020-09-08 5:30:00 -0800
description: Oregon fires 2020 # Add post description (optional)
img: oregon-fires-cover.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [oregon, fire, timelapse, qgis, goes-17, nasa]
youtubeId: Kf2JU_2TmjY
---

On September, 8, 2020 conditions were just right to cause one of the worst fires on record in Oregon history. Over 1 million acres burned up and air quality for much of the state was hazardous for weeks afterward because of all of the smoke.

This is what it looked like outside (no camera filters), it was darker red closer to the fires in Salem.

![Oregon Smoke]({{site.baseurl}}/assets/img/oregon-fires-smoke.jpg)

### Gathering Data:

I wanted to see what the progress of the fire looked like over time so I located some data to help create a timelapse.

The Geostationary Operational Environmental Satellite (GOES) is a satellite or rather a constellation of geostationary satellites that pull in various forms of data that are used by scientific and meterological groups.

The GOES-17 satellite takes a picture of the Pacific Ocean and the Western US roughly every 5-15 minutes depending on the mode the imager is running. There are archives of scientific netcdf data but when generating timelapses it can be burdensome to process that much data on consumer based computers. Thankfully NASA developed a Web Map Tile Service called Global Imagery Browse Services (GIBS) where you can pull in a feed of recent satellite imagery that can be coupled with QGIS' temporal controller to generate a frames for a timelapse.

This is the endpoint to add the wmts in QGIS:

```
https://gibs.earthdata.nasa.gov/wms/epsg4326/best/wms.cgi
```

In my case I was looking for the visible spectrum to see the smoke along with some hot spots from the MODIS satellite that highlights potential fires.

These were the GIBS layers I used:

- Thermal Anomalies and Fires (375m, All, VIIRS, NOAA20)
- Red Visible (0.64 µm, Band 2, ABI, GOES-West)

I also pulled in the PM 2.5 data (example file US-20090600_pm25.grib2) from the EPA to highlight how bad the air quality was.

[Airnow Hourly Data](http://files.airnowtech.org/?prefix=airnow/2020/)

I then put them all together and set up the temporal controller in QGIS to spit out a frame every 10 minutes to match the frequency of satellite imagery changes. Once the frames were all generated I used ffmpeg to combine them all together and shotcut to add a title and music to upload to youtube.

This is the result:

{% include youtubePlayer.html id=page.youtubeId %}
