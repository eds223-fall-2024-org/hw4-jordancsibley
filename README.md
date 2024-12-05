# Investigating Potential Aquaculture Sites Along the West Coast

### Environmental Data Science, HW #4

## Description 

This project identifies potential aquaculture sites for oysters and sugar kelp along the West Coast of the United States. Raster data on sea surface temperature and depth are combined and resampled to map suitable sites based on species-specific thresholds. Additionally, a custom function is developed that allows users to input a species name along with its preferred depth and temperature ranges. This function generates a suitability map and a corresponding area table, making it adaptable for evaluating other species.

## Analysis Highlights 
- **Processing and cleaning spatial data**: Produces code that matches the coordinate reference systems  (`terra::project()` and `st_transform()`), resolution (`terra::resample()`), and extent (`terra::crop()`) of all the spatial data
- **Resampling raster data**: Rasters are resampled using a reclassification matrix and `terra::classify()` to indicate the suitable cells in the sea surface temperature and depth rasters. 
- **Map algebra**: Map algebra is applied to rasters to find the mean sea surface temperatures from 2008-2012, and `terra::lapp()` is used to apply a function to the layers of a stacked raster to find cells that are suitable for both depth and temperature. 
- **Function creation**: A custom function that takes species-specific depth and temperature requirements to identify suitable aquaculture sites. The function generates both a suitability map and a table for better visualization of the results. The `tmap` and `kableExtra` packages are used to create the maps and tables, respectively.

## Repository Structure
```
EDS223-HW4
│   README.md
│   .gitignore
│   HW4.qmd
|   HW4.html
│   EDS223-HW4.Rproj    
│
└───data
    └───average_annual_sst_2008.tif
    └───average_annual_sst_2009.tif
    └───average_annual_sst_2010.tif
    └───average_annual_sst_2011.tif
    └───average_annual_sst_2012.tif
    └───depth.tif
    └───wc_regions_clean.dbf
    └───wc_regions_clean.prj
    └───wc_regions_clean.shp
    └───wc_regions_clean.shx
```  


## Data Access 

Sea surface temperature data from 2008 to 2012 generated from [NOAA's 5km Daily Satellite Sea Surface Temperature Anomaly v3.1](https://coralreefwatch.noaa.gov/product/5km/index_5km_ssta.php)

Bathymetry data comes from [General Bathymetric Charts of the Oceans (GEBCO)](https://www.gebco.net/data_and_products/gridded_bathymetry_data/#area)

The designation of Exclusive Economic Zones off the West Coast comes from [Marineregions.org](https://www.marineregions.org/eez.php), which outlines the boundaries of marine biogeographic areas. \[3\] The names of the regions are: Washington, Oregon, Northern California, Central California, and Southern California.

All of the data needed for this project can be found in the `data` folder within the repository. 

## Author 

Jordan Sibley 

Master of Environmental Science Student at the Bren School of Environmental Science & Management

jcsibley@bren.ucsb.edu

jordan.c.sibley@gmail.com 

## Acknowledgements 

Ruth Oliver created this assignment for the course: Environmental Data Science 223 Geospatial Analysis & Remote Sensing at the Bren School of Environmental Science & Management at the University of California, Santa Barbara. The assignment description is found [here](https://eds-223-geospatial.github.io/assignments/HW4.html)

## References 
1.  NOAA Coral Reef Watch. 2008-2012, updated daily. NOAA Coral Reef Watch Version 3.1 Daily 5km Satellite Regional Virtual Station Time Series Data for Southeast Florida, Mar. 12, 2013-Mar. 11, 2014. College Park, Maryland, USA: NOAA Coral Reef Watch. Data set accessed 2024-11-12 at https://coralreefwatch.noaa.gov/product/vs/data.php.

2.  GEBCO Compilation Group (2024) GEBCO 2024 Grid (doi:10.5285/1c44ce99-0a0d-5f4f-e063-7086abc0ea0f)

3.  Flanders Marine Institute (2024): MarineRegions.org. Available online at www.marineregions.org. Consulted on 2024-11-13.


