---
layout: post
title: Indoor Maps
date: 2020-11-03 5:30:00 -0800
description: Indoor Maps # Add post description (optional)
img: indoor-maps-cover.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [leaflet, indoor, maps]
---

I've mapped a lot of external landscaping and utility data but haven't done as much with indoor maps. I delved into a few indoor mapping projects in university with the library floor plans, but there were some issues with data consistency and georeferencing that made it challenging. 

Instead of going through the whole process of georeferencing something with a high level of precision with the relatively small footprint of a floorplan, I thought that this would be a fun experiment to try out a relative coordinate system that isn't directly tied to the planet i.e. a non-geographical coordinate system. 

This is fundamentally similar to the [Hubble Legacy Field](https://anthonyblackham.com/hubble-legacy-field/) project that I did but it goes a few steps further in creating more interactive features.

There are multiple ways this could be accomplished but I'm going to go step by step on how I created the following map using Leaflet:

<div class="embed-container">
  <iframe
      src="https://anthonyblackham.github.io/floorplans"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="">
  </iframe>
</div>

### Initialize map with a simple coordinate system.

I started the map using [this guide](https://leafletjs.com/examples/crs-simple/crs-simple.html) from the leaflet docs. 

Code:

Default html code:

```html
<!DOCTYPE html>
<html>
   <head>
      <style></style>
   </head>
   <script></script>
   <body></body>
</html>
```
We'll add some configs, a title, and the leaflet libraries in the head:

```html
<!DOCTYPE html>
<html>
<head>
	
	<title>Non Geographic Map</title>

	<meta charset="utf-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	
	<link rel="shortcut icon" type="image/x-icon" href="docs/images/favicon.ico" />

	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A==" crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js" integrity="sha512-XQoYMqMTK8LvdxXYG3nZ448hOEQiglfqkJs1NOQV44cWnUrBc8PkAOcXy20w0vlaXaVUearIOBhiXZ5V3ynxwA==" crossorigin=""></script>
</head>
```

Next we'll add the map  div and initialize a basic map, and we'll also add some style confnigs to open it full screen

```html
<!DOCTYPE html>
<html>
<head>
	
	<title>Non Geographic Map</title>

	<meta charset="utf-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	
	<link rel="shortcut icon" type="image/x-icon" href="docs/images/favicon.ico" />

	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A==" crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js" integrity="sha512-XQoYMqMTK8LvdxXYG3nZ448hOEQiglfqkJs1NOQV44cWnUrBc8PkAOcXy20w0vlaXaVUearIOBhiXZ5V3ynxwA==" crossorigin=""></script>

	<style>
		html, body {
			height: 100%;
			margin: 0;
		}
		#map {
			width: 100%;
			height: 100%;
		}
}
	</style>

</head>

<body>

<div id='map'></div>

<script>

//define the map using a simple coordinate system

	var map = L.map('map', {
		crs: L.CRS.Simple,
		minZoom: 0,
	});

</script>

</body>
</html>
```

It should show just a basic map window but we haven't added anything to the map yet. Let's create a polygon representing a building footprint and add it to the map. Since we aren't using typical latitude longitude units I'm setting an arbitrary scale that one map unit = one foot. One important thing to note is that the default coordinate system for leaflet is (y, x) or longitude, latitude, rather than (x, y)

```html
var firstfloor = L.polygon([
	[0,  0],
	[50.5,  0],
	[50.5, 17],
	[31.5, 17],
	[31.5, 19],
	[12, 19],
	[12, 17],
	[8, 17],
	[4, 17],
	[4, 13],
	[0, 13]
],
```

add some style

```html
{color: 'black',
fillColor: 'white',
fillOpacity: 1}
```
add it to the map:
```html
).addTo(map)
```

add a popup to your new feature:
```html
.bindPopup("First Floor");;
```



we can calculate the center of the footprint and set the map to the middle when it first loads, variables are (y, x, zoom level)

```html
map.setView([25.25, 9.5], 3);
```
this is the full HTML code so far:

```html
<!DOCTYPE html>
<html>
<head>
	
	<title>Non Geographic Map</title>

	<meta charset="utf-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	
	<link rel="shortcut icon" type="image/x-icon" href="docs/images/favicon.ico" />

	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A==" crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js" integrity="sha512-XQoYMqMTK8LvdxXYG3nZ448hOEQiglfqkJs1NOQV44cWnUrBc8PkAOcXy20w0vlaXaVUearIOBhiXZ5V3ynxwA==" crossorigin=""></script>

	<style>
		html, body {
			height: 100%;
			margin: 0;
		}
		#map {
			width: 100%;
			height: 100%;
		}
}
	</style>

</head>

<body>

<div id='map'></div>

<script>

//style 

var footprintStyle = {
	color: 'black',
	fillColor: 'white',
	fillOpacity: 1
};

//define the map using a simple coordinate system

	var map = L.map('map', {
		crs: L.CRS.Simple,
		minZoom: 0,
	});

var firstfloor = L.polygon([
	[0,  0],
	[50.5,  0],
	[50.5, 17],
	[31.5, 17],
	[31.5, 19],
	[12, 19],
	[12, 17],
	[8, 17],
	[4, 17],
	[4, 13],
	[0, 13]
],
footprintStyle
).addTo(map).bindPopup("First Floor");;


	map.setView([25.25, 9.5], 3);

</script>

</body>
</html>
```

The source data can be found at my repository [here](https://github.com/anthonyblackham/floorplans)
