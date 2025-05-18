# Geospatial Land Suitability Assessment for Water harvesting structures

This repository introduces a Python Jupyter Notebook code cells for geospatial analysis and land suitability assessment. This script makes use of powerful libraries (e.g., Rasterio, PyProj, NumPy, Pandas, Matplotlib, and OWSLib) to do the following:
- **Loading the DEM, display metadata from xml file** & Creating figure with three subplots (Raster Plot + Histogram Plot + Histogram Table)
- **Calculating slope from DEM & similarly creating three subplots** for visualization
- **Performing IDW interpolation** on rainfall and temperature csv with same cell size as DEM
- **Clip and resample rasters** LULC data to match a reference DEM’s extent, resolution, and coordinate system.
- **Compute and display classification statistics** of a land cover raster.
- **Perform a land suitability evaluation** using the Analytical Hierarchy Process (AHP) technique. This includes calculating weights via eigenvector analysis from a pairwise comparison matrix and using a weighted overlay approach.
- **Generate informative tables** that display AHP weights and LULC class statistics (with class names extracted from an attached Excel file).

---

## Table of Contents

- [Introduction](#introduction)
- [Code Overview](#code-overview)
- [Data](#data)
- [License](#license)


---

## Introduction
- **Performing a weighted overlay assessment** using multiple spatial layers—like elevation, slope, rainfall, temperature, and land use/land cover (LULC)—requires careful preprocessing, reclassification, weight assignment, and aggregation.
- **Integration of Multiple Criteria** Weighted overlay allows each criterion (e.g., elevation, slope, rainfall, temperature, LULC) to be reclassified on a common suitability scale. The important aspect is that each factor is standardized before the overlay. This ensures that different units (meters, degrees, mm, °C, or categorical values) can be integrated into a single composite score.
  - **Elevation and Slope:** Affect water drainage and soil depth.
  - **Rainfall and Temperature:** Determine the climatic suitability, water availability, and growing period.
  - **LULC:** Reflects current land use patterns and potential for modification or protection
- **Weight Assignment:** The relative importance of each factor must be determined. - Analytic Hierarchy Process (AHP): Use pairwise comparisons to systematically derive weights. For instance, one might determine that rainfall and temperature combined could represent 40%–50% of the overall suitability, while slope might contribute 20%, elevation 15%, and LULC 15%.
- **Weighted Summation Equation:** Once you have reclassified each raster into a common scale (each cell with a standardized suitability score) and assigned a weight to each layer, combine them using a weighted sum.
- **Mapping:** Visualize the final suitability raster using appropriate color ramps that clearly delineate different suitability levels (e.g., highly suitable, moderately suitable, marginal, or unsuitable). Include appropriate legends, scale bars, and annotations so decision makers can easily interpret the results.


---

## Code Overview
-  Importing all the necessary Python libraries for spatial data processing, geospatial analysis, raster operations, array computations, and plotting.
-  Loading the Digital Elevation Model (DEM) from a GeoTIFF file and display its metadata using xml file
-  Plotting the Elevation raster, histogram & table
-  Calculating slope from the elevation raster, plotting the slope, histogram & table
-  Loading & plotting rainfall data overlayed on elevation raster
-  Performing the IDW interpolation on rainfall observations
-  Loading & plotting temperature data overlayed on elevation raster
-  Performing the IDW interpolation on temperature observations
-  Loading & plotting LULC and its class statistics
-  **FINAL SUITABILITY ASSESSMENT**
   - Checking the metadata of rasters for assessment
   - Computing AHP weights
   - Performing Weighted Overlay & creating a composite suitability map by summing each criterion multiplied by its weight.
   - Plotting the Composite Suitability Map


---

## Data
- Data can be downloaded from this gdrive [link](https://drive.google.com/drive/folders/1O0YRAsxTTXQj8nR89inrfkpVmIjmRCoa?usp=sharing)
