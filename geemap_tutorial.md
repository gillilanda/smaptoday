---
title: Python Tutorial 
layout: home
nav_order: 4
---

## Accessing, Analyzing, and Visualizing SMAP data in the Cloud

This tutorial is designed to analyze and visualize data from the Soil Moisture Active Passive (SMAP) mission available on Google Earth Engine's cloud. The [geemap](https://geemap.org/) Python library allows users to access Google Earth Engine SMAP data, conduct their analysis, and visualize the data all without downloading anything to their local machine. SMAP data is traditionally available through the [National Snow and Ice Data Center](https://nsidc.org/data/smap) via NASA's Earthdata Search, the CMR archive, and direct cloud access on Amazon Web Services (AWS), all of which require either downloading or paying for cloud processing. The advantage of Google Earth Engine is that it currently allows cloud processing free of charge for academic research and education. 

The code included in this tutorial is available as a Jupyter Notebook in my GitHub [geol5093 repository](https://github.com/gillilanda/geol5093/blob/main/GEOL5093_notebook.ipynb). 

## Prerequisites
1. Setup a [Google Earth Engine](https://earthengine.google.com/) account and set up a cloup project. Make note of your cloud project ID.
2. Install the geemap Python library (plus any others not already installed)

## Import Libraries


```python
import ee
import geemap
import geopandas
import numpy as np
import matplotlib as plt
```

## Authenticate GEE account and Initialize project 


```python
ee.Authenticate()
ee.Initialize(project='project ID')
```

## Change variables with desired dates, bands, and output file paths


```python
gee_proj_id= 'project-ID'
start_date='2025-11-01'
end_date='2025-11-30'
band_selection= 'sm_rootzone'
# add _mean to the original band name
mean_band_selection='sm_rootzone_mean'
output_stats = " /path.csv" 
output_raster= "/path.tif"
```

## Function to calculate zonal statistics and export to a file


```python
# IN PROGRESS - figure out how to print the statistic value instead of downloading a single CSV

def get_mean(raster, zones, output_file):
    """Input raster, zone (or study region), output file path, statistic type, and scale. Allowed output formats: csv, shp, json, kml, kmz. Allowed statistics type: MEAN, MAXIMUM, MINIMUM, MEDIAN, STD, MIN_MAX, VARIANCE, SUM """    
    zone_stats = geemap.zonal_stats(raster, zones, output_file, stat_type="MEAN", scale=1000)
    return print(zone_stats)
```

## Load SMAP data from GEE and explore available bands 


```python

smap_collection = (
    ee.ImageCollection('NASA/SMAP/SPL4SMGP/008')
    .filterDate(start_date, end_date)
)
smap_collection

```

## Select band
Select a single band to focus statistics (selected above) on, then apply the mean reducer function, which calculates the mean raster of your selected band.


```python
# Select one band to focus on
smap_bands = smap_collection.select([band_selection])

# Apply Mean Reducer - this calculates the mean raster of your selected band
mean_smap_raster = smap_bands.reduce(ee.Reducer.mean())
```

## Choose clipping area
Load the US states you would like to clip the data to. All lower 48 US states are included by default. 


```python
# Load the states you would like to clip your data to

states = ee.FeatureCollection("TIGER/2018/States")
lower48 = states.filter(ee.Filter.inList('NAME', [
    'Alabama', 'Arizona', 'Arkansas', 'California', 'Colorado', 'Connecticut', 
    'Delaware', 'Florida', 'Georgia', 'Idaho', 'Illinois', 'Indiana', 'Iowa', 
    'Kansas', 'Kentucky', 'Louisiana', 'Maine', 'Maryland', 'Massachusetts', 
    'Michigan', 'Minnesota', 'Mississippi', 'Missouri', 'Montana', 'Nebraska', 
    'Nevada', 'New Hampshire', 'New Jersey', 'New Mexico', 'New York', 
   'North Carolina', 'North Dakota', 'Ohio', 'Oklahoma', 'Oregon', 'Pennsylvania', 
    'Rhode Island', 'South Carolina', 'South Dakota', 'Tennessee', 'Texas', 
    'Utah', 'Vermont', 'Virginia', 'Washington', 'West Virginia', 'Wisconsin', 
    'Wyoming'
]))

country_geometry = lower48.union()
```

## Calculate mean of all band pixel values 
Output data is a single value representing the mean rootzone soil moisture of all pixels in the monthly mean raster calculated above


```python
get_mean(mean_smap_raster, country_geometry, output_stats)
```

## Create a visualization of sm_rootzone in the lower 48 states


```python
m = geemap.Map(center=[40, -100], zoom=4)
clipped_image =  mean_smap_raster.clip(country_geometry)

#select the SMAP band to visualize and color palette
vis_params = {
    'bands': [mean_band_selection],
    'min': 0,
    'max': 0.9,
    'palette': 'Spectral',
}
m.add_layer(clipped_image, vis_params, 'Mean SM')
m
```

## Download the mean raster to your computer (must clip to bounding box - working on this to clip to image collection)
In progress - figure out how to clip to the state boundaries instead of the bounding box



```python
roi = ee.Geometry.Rectangle([-124.848974, 24.396308, -66.885444, 49.384358])
geemap.ee_export_image(clipped_image, filename=output_raster, scale=2000, region=roi)
```
----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
