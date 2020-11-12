---
layout: post
title: Hubble Legacy Field
date: 2019-05-11 5:30:00 -0800
description: Exploring the Hubble Legacy Field # Add post description (optional)
img: hubble-legacy-field-cover.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [hubble, nasa, space, gdal, leaflet]
---

In 2019 NASA released 16 years worth of hubble discoveries in one large image (1.2 GB!) that shows roughly 265000 galaxies. The area is roughly what your thumbnail would cover with your arm extending looking at the sky. They named it the [Hubble Legacy Field](https://hubblesite.org/image/4492/news). It's enough to make one feel quite insignificant in the universe.

To fully experience the scale, the full resolution image should be viewed, however many people view content on phones that lack the memory and processing power to view a 25500x25500 resolution image.

I found a solution that cuts the large image into smaller images. Those smaller images (called tiles) are generated dynamically in a leaflet based web map. This is the same underlying principle that Google Maps use.

Here is the result:

<div class="embed-container">
  <iframe
      src="https://anthonyblackham.github.io/HubbleLegacyField/"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

### Gathering Sources:

The first step was to download the large image from [here](https://hubblesite.org/image/4492/news)

The second step was to get the [gdal2tiles]((https://github.com/commenthol/gdal2tiles-leaflet)) library that converts the image into tiles and subsequently host them on a web map

Dependencies:

```
sudo apt install python3-gdal
```

```
git clone https://github.com/commenthol/gdal2tiles-leaflet.git
```

### Creating the Map

This is the command for the python library to generate the tiles:

```
gdal2tiles.py -l -p raster -z 0-5 -w none <image> <tilesdir>
```

Typically earth based web maps have a standard projection and standard zoom levels depending on the resolution of the data. However in this case we are looking at space where there isn't a standard projection. We will need to create zoom levels based on the dimensions of the image instead.

In order to determine the zoom (-z) factor, we will use the formula: `log2(max(width, height)/tilesize)`

Since our image is 25500 our equation we can run in the terminal is

```
echo "l(25500/256)/l(2)" | bc -l
```

This equals 6.64, so you round up to 7, and our zoom factor will be `-z 0-7`

So our final command will be:

```
gdal2tiles.py -l -p raster -z 0-7 -w none STSCI-H-p1917a-f-25500x25500.tif tiles
```

The easiest way to generate it is to replace the contents of the `test` folder with your own images and then modify the contents of the `createtiles.sh` with the above command and it should spit out a final folder of tiles and an HTML with a full Leaflet integration. These files can be pushed to github pages or standalone sites (with a few minor tweaks for base urls).

### Source Files

The data used to create the web map can be found at my repository [here](https://github.com/anthonyblackham/HubbleLegacyField)
