# NDVI-For-Mombasa-GEE

 The coordinates of Mombasa were approximated as:

Longitude: 39.57 to 39.75
Latitude: -4.14 to -3.96
This rectangle represents an approximate bounding box around the Mombasa region.

javascript
Copy code
var mombasaGeometry = ee.Geometry.Rectangle([39.57, -4.14, 39.75, -3.96]);
Map.centerObject(mombasaGeometry);
This created a geometry object that precisely defined the area of interest (Mombasa) based on its geographic location, without needing to reference the FAO/GAUL dataset's administrative boundaries.

Using the Defined Geometry: After defining the mombasaGeometry bounding box, the script uses this geometry to filter the Sentinel-2 image collection (filteredS2) based on its bounds, clip the satellite data to that geometry, and visualize it. This is done for both the RGB and NDVI layers:

The Sentinel-2 images were filtered using ee.Filter.bounds(mombasaGeometry) to ensure that only images that overlap with the Mombasa region were selected.
The composite (RGB and NDVI) images were clipped to the mombasaGeometry to ensure they are only shown within the Mombasa area.
Visualizing NDVI: Finally, the NDVI (Normalized Difference Vegetation Index) was calculated for each image, and the NDVI composite was visualized using a color palette that represents vegetation health (from red for low vegetation to green for high vegetation).

Why This Worked:
Manual Geometry Override: By manually defining a geometry for Mombasa, we bypassed the reliance on the administrative boundary data (which might have been incomplete or inconsistent for Mombasa). This allowed the script to focus directly on the geographic area of interest.

Flexibility: Earth Engine allows you to define any geometry (a point, polygon, or rectangle) directly, making it flexible for cases where administrative data is not available or inconsistent.

Summary of the Workflow:
Manual geometry for Mombasa was defined to specify the region.
Sentinel-2 data was filtered and processed using this geometry.
RGB and NDVI composites were generated for Mombasa.
Visualization was added to the map with appropriate color palettes for the image and NDVI.




![Image](https://github.com/user-attachments/assets/4d4c72a9-a305-4f4a-9939-33f709fa9638)



![ndvi](https://github.com/user-attachments/assets/e2d57e9e-07da-4129-81e0-ccaf1e50807b)



![ee-chart](https://github.com/user-attachments/assets/87bdf5fd-b799-4283-91c5-edcede53c202)
