# Urban Green Space and Urban Heat

A multi-city spatial analysis of the relationship between urban greenness (NDVI)
and land surface temperature (LST) across ten major U.S. cities, with an analysis
of how green space is distributed across income levels.

## Summary

Cities experience the urban heat island effect: built-up areas run hotter than
their surroundings, and vegetation is one of the main things that cools them down.
This project quantifies that relationship at the neighborhood (census-tract) level,
then asks whether green space, and the cooling it provides, is distributed equitably.

**Key findings**
- A consistent negative relationship between greenness and surface temperature
  across all ten cities: greener neighborhoods are cooler.
- The effect is strongest in inland cities (Philadelphia, San Antonio, San Jose:
  R² > 0.3, cooling of 10–17°C per NDVI unit) and weakest in ocean-moderated
  coastal cities (San Diego, Los Angeles).
- The least-green neighborhoods run 4–7°C hotter than the greenest ones.
- Green space is not equitably distributed: in several cities, lower-income
  neighborhoods have both less vegetation and higher temperatures.
  
![NDVI vs LST by city](figure_ndvi_lst.png) 

## Data

- **NDVI** — MODIS MOD13Q1, July 2022, 250 m resolution
- **LST** — MODIS MOD11A2, July 2022, 1 km resolution
- **Census tracts** — 2020 TIGER/Line shapefiles
- **Income** — 2020 ACS 5-year estimates (median household income, B19013_001)

Cities analyzed: New York, Los Angeles, Chicago, Houston, Phoenix, Philadelphia,
San Antonio, San Diego, Dallas, San Jose.

## Method

NDVI and LST rasters were pulled from Google Earth Engine, masked to each city's
census tracts, and reduced to per-tract means via zonal statistics. Income data
were joined at tract level. For each city I computed NDVI–LST correlations and
linear fits, an income–NDVI analysis (six cities with sufficient data), and a
decile analysis of LST across NDVI deciles.

**Stack:** R — `sf`, `terra`, `exactextractr`, `tidycensus`, `ggplot2`

## Files

- `Project.Rmd` — full analysis (data processing, models, figures)
- `Project_report.pdf` — written report with results and discussion

## Limitations

Single summer month (limited temporal generalizability); incomplete ACS income
data for some cities; simple linear models only. Future work: multi-season data,
spatial/non-linear models.

## Author

Leonardo Gravellone — MSc Management & Informatics, USI Lugano