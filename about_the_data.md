---
title: About the Data
layout: home
nav_order: 3
---
The Soil Moisture Active Passive (SMAP) NASA satellite mission launched in 2015 and continues collecting data to the present day. A majority of the SMAP mission data products are long-term and derived from L-band radiometer brightness temperature data. Shortly after the satellite was launched in March 2015, the L-band radar instrument failed, leaving only 5 months of radar-derived SMAP data. The radiometer instrument measures the naturally occurring radio frequency (within L-band frequencies) emitted from the Earth. The L-band frequency is not affected by cloud cover, weather, or most vegetation. Within the L-band frequency, water-saturated soil is measured as "warm" while dry soil is measured as "cold". The SMAP instrument has a sun-synchronous polar orbit and a revisit time of 2 days in polar regions and 3 days near the equator. 

The SMAP mission provides global measurements of soil moisture and freeze-thaw conditions to better understand how Earth’s water, energy, and carbon cycles interact and influence climate and ecosystems. SMAP's scientific objectives include improving knowledge of how these cycles are linked, estimating water and energy movement at the land surface, and quantifying carbon flux, including sensitive boreal regions where frozen or thawed ground greatly affects carbon release. SMAP helps enhance weather and climate prediction, supports flood forecasting, and drought monitoring. Overall, the mission aims to reduce uncertainties in environmental models and improve understanding of how Earth’s systems respond to natural variability and climate change.

<img width="600" height="452" alt="SMAP_data_orbit" src="https://github.com/user-attachments/assets/6013c06c-83f5-4dc7-83f3-4d7cff280bb5" />

*Credit: NASA JPL*

For this study, I focus on the *SMAP L4 9 km EASE-Grid Surface and Root Zone Soil Moisture Geophysical Data, Version 8* (SPL4SMGP) data product. SPL4SMGP includes multiple soil moisture parameters, including surface soil moisture (0-5cm), rootzone soil moisture (0-100cm), and profile soil moisture (0-bedrock depth cm). The data have a spatial resolution of 9km x 9km and consist of 3-hourly time-averaged science parameters, resulting in about 8 global data files per day.

---
References 
- Entekhabi Dara, N.J., Njoku, E.G., O’Neill, P.E., et al., 2010, The Soil Moisture Active Passive (SMAP) mission: Proceedings of the IEEE, v. 98, no. 5, p. 704–716, https://doi.org/10.1109/JPROC.2010.2043918.
- National Aeronautics and Space Administration (NASA), n.d., SMAP multimedia: Jet Propulsion Laboratory, available at https://smap.jpl.nasa.gov/multimedia/age=0&per_page=25&order=created_at+desc&search=&href_query_params=category%3Dimages&condition_1=1%3Ais_in_resource_list&category=51%2C53 (last accessed April 19, 2026).
- Reichle, R.H., G. De Lannoy, R.D. Koster, W.T. Crow, J.S. Kimball, Q. Liu, and M. Bechtold. 2025. SMAP
L4 Global 3-hourly 9 km EASE-Grid Surface and Root Zone Soil Moisture Geophysical Data, Version 8.
SPL4SMGP. Boulder, Colorado, USA. NASA National Snow and Ice Data Center Distributed
Active Archive Center. https://doi.org/10.5067/T5RUATAQREF8.(last accessed April 20, 2026)
----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
