# Observer-Based Point Cloud Viewshed

Project for exploring stacs and COGs. This project computes and visualizes the viewshed (visible terrain) from a given observer location using high-resolution DEM data (3DEP or NASADEM) and point cloud analysis. It generates both 2D and 3D visualizations of visible terrain, horizon profiles, and more. The tools is very realistic in terms of blocking elevation, therefore some results may be unsatisfying to look at. I would additionally like to extend this to include some bathymetry datasets as well. Currently the script excludes continous flat terrain from plotting for brevity which needs some adjustment. 

![image](https://github.com/user-attachments/assets/03a89301-c519-488f-94af-c81995dafd9e)

![image](https://github.com/user-attachments/assets/0648aeb1-6ffa-42aa-b709-8c9e97f3d4df)

## Features

- Downloads and mosaics DEM tiles from Microsoft Planetary Computer.
    - 3DEP proritized for higher resolution in CONUS.
    - NASADEM fallback when 3DEP unavailable and outside CONUS
- Projects observer location to UTM and extracts DEM window
- Vectorized computation of visible points and horizon angles for all azimuths
- Multiple visualizations:
  - DEM hillshade with visible points (Cartesian and polar)
  - Viewshed mask overlay
  - Horizon and elevation profiles vs. azimuth
  - 3D cylindrical plot of visible points

## Requirements

- Python 3.8+
- [NumPy](https://numpy.org/)
- [Pandas](https://pandas.pydata.org/)
- [Rasterio](https://rasterio.readthedocs.io/)
- [pyproj](https://pyproj4.github.io/pyproj/)
- [pystac-client](https://pystac-client.readthedocs.io/)
- [planetary-computer](https://planetarycomputer.microsoft.com/docs/reference/sdk/)
- [matplotlib](https://matplotlib.org/)

Install dependencies with:

```sh
pip install numpy pandas rasterio pyproj pystac-client planetary-computer matplotlib
```

## Usage

1. **Set Observer Parameters**

   Edit the observer latitude, longitude, and eye height at the top of [Observer_based_pointcloud_viewshed.ipynb](Observer_based_pointcloud_viewshed.ipynb):

   ```python
   obs_lat = 42.940389
   obs_lon = -122.107171
   eye_height = 1.80
   ```

2. **Run the Notebook**

   Open [Observer_based_pointcloud_viewshed.ipynb](Observer_based_pointcloud_viewshed.ipynb) in Jupyter or VS Code and run all cells.

3. **Visualizations**

   The notebook will generate:
   - DEM hillshade with visible points (Cartesian and polar)
   - Viewshed mask overlay (green = visible, red = not visible)
   - Horizon angle and elevation profiles vs. azimuth
   - 3D cylindrical plot of visible points

## Customization

- Adjust `max_vis` and `padding` for the maximum visibility radius and DEM window size.
- Change `azimuths`, `angle_step`, or `r_step` for finer or coarser sampling.
- Modify plotting code for custom visualizations.

## Data Sources

- [3DEP Seamless DEM](https://planetarycomputer.microsoft.com/dataset/3dep-seamless)
- [NASADEM](https://planetarycomputer.microsoft.com/dataset/nasadem)


