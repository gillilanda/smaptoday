---
title: Python Tutorial 
layout: home
nav_order: 3
---

This tutorial is designed to analyze and visualize data from the Soil Moisture Active Passive (SMAP) mission available on Google Earth Engine. The [geemap](https://geemap.org/) Python library allows users to access Google Earth Engine SMAP data, conduct their analysis, and visualize the data all without downloading anything to their local machine. SMAP data is traditionally available through the [National Snow and Ice Data Center](https://nsidc.org/data/smap) via NASA's Earthdata Search, the CMR archive, and direct cloud access on Amazon Web Services (AWS), all of which require either downloading or paying for cloud processing. The advantage of Google Earth Engine is that it currently allows cloud processing free of charge for academic research and education. 

The code included in this tutorial is available as a Jupyter Notebook in my GitHub [geol5093 repository](https://github.com/gillilanda/geol5093/blob/main/GEOL5093_notebook.ipynb). 


```import ee
import geemap
import geopandas
import numpy as np
import matplotlib as plt
```

```
# Trigger the authentication flow.
ee.Authenticate()

# Initialize the project with your cloud project ID
ee.Initialize(project='forward-aura-488318-c0')
```

```
start_date='2015-11-01'
end_date='2015-11-30'
band_selection= 'sm_rootzone'
mean_band_selection='sm_rootzone_mean'
output_stats = "/Users/amgi2571/Desktop/Spring 2026/remote sensing envi/final_proj/colorado_smap_zonal_stats_2015.csv" 
output_raster= "/Users/amgi2571/Desktop/Spring 2026/remote sensing envi/final_proj/colorado_sm_mean_2015.tif"
```

----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
