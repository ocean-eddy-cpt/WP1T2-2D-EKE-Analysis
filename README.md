# along-track-altimetry-analysis
This repository contains code written to parse and analyze along-track sea surface height measurements collected by various satellite altimeters (Jason-2, Sentinel-3A, etc). Data are accessed on Pangeo and processed to explore spatial and temporal variability along each satellite track. This repository includes:

- altimetry_tools.py (library of functions called by master function global_along_track.ipynb)
- **global_along_track.ipynb** (master function to filter all tracks, grid, and partition in time) 
- aviso_filter.ipynb (2d filtering using kernels developed for gcm-filters )
- aviso_ke.nc (data file for aviso_filter.ipynb)
- global_along_track.ipynb (working noteboook, not well documented)
- initial_processing.ipynb (prep each track for filtering, grid as desired, etc)
- j2_global_ke_mke_eke_140.nc (output file from global_along_track.ipynb) 
- n_atl_along_track_sla.ipynb (working notebook, not well documented)

One-dimensional spatial filtering is carried out using filter kernerls defined in "Diffusion-based Smoothers for Spatial Filtering of Gridded Geophysical Data" [doi: https://doi.org/10.1029/2021MS002552].

For purposes of recreating figures and analysis described in "On the Observed Seasonality of the Mesoscale Inverse Cascade in the Global Ocean" [pre-print: https://doi.org/10.1002/essoar.10508837.1], global_along_track.ipynb is the reference notebook. This notebook is heavily annotated to describe analysis procedures and considers the effect of different spatial filter kernel choices (taper, Gaussian, boxcar). In addition, we filter cross-track geostrophic velocites using a spatially varying filter scale equal to the length in kilometers of 1 degree of longitude. This is done to provide maps of mean and eddy kinetic energy with a resolution equal to a global climate model. Seasonality is considered, specifically what fraction of seasonally varying kinetic energy is 'lost' when filtering to 1 degree.      
