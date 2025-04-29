# Wildfire Data Scraping & Mapping for Geospatial Analysis

This project uses the FIRMS (Fire Information for Resource Management System) API and Google Earth Engine (GEE) to scrape, process, and visualize wildfire data for Canada. The workflow includes downloading recent MODIS wildfire data, filtering and clipping it to Canadian boundaries, and visualizing spatiotemporal fire patterns with GeoPandas and Matplotlib.

This script was developed as a requirement for the Graduate Certificate in GIS at the Centre of Geographic Sciences, NSCC, Lawrencetown, Nova Scotia.

For educational purposes only.
© 2025 COGS. Created by Brian Gauthier, April 7, 2025.

## Features

- Accesses MODIS NRT wildfire data from FIRMS
- Clips fire detections to Canada's national boundary using GEE
- Filters fire detections by confidence and Fire Radiative Power (FRP)
- Differentiates between daytime and nighttime detections
- Converts UTC datetimes to Canadian time zones (Halifax, Toronto, Vancouver)
- Visualizes fire data by time since detection (e.g., <1hr, 1–4hr, etc.)

## Setup

### Requirements

Install the following Python packages:

```bash
pip install earthengine-api geopandas matplotlib pandas shapely pytz
```

You also need:

- A [FIRMS MAP_KEY](https://firms.modaps.eosdis.nasa.gov/api/) (register for access)
- An authenticated Google Earth Engine environment (`ee.Authenticate()`)

### Earth Engine Setup

```python
import ee
ee.Authenticate()
ee.Initialize(project='your-project-name')  # Replace with your Google Cloud Project name
```

### FIRMS API Key Setup

```python
MAP_KEY = "your-FIRMS-mapkey-here"
```

## Usage

The workflow is organized into sections in the Jupyter Notebook:

1. **Import & Setup** – Load libraries, authenticate Earth Engine, and configure environment
2. **Data Access** – Query MODIS data from FIRMS for the past 7 days
3. **Geo-processing** – Convert to GeoDataFrame, clip to Canada, and assign CRS
4. **Visualization** – Plot fire detections over Canadian boundary
5. **Day/Night Filtering** – Filter detections by confidence, FRP, and time of day
6. **Datetime Analysis** – Convert and analyze acquisition time across multiple time zones
7. **Recency Classification** – Classify detections based on time since occurrence

## Example Output

- Total number of fire detections over Canada
- Maps showing day vs night detections
- Time-zone adjusted datetime summaries
- Heat maps by detection recency

## Notes

- The dataset updates frequently; rerun to fetch latest data
- FIRMS transaction limits may apply — monitor usage in the script

## License

MIT License
