# Raster Comparison & IoU Visualization

The `plot_ground_truth` function is a geospatial utility designed to evaluate the accuracy of segmentation models or remote sensing outputs. It performs a side-by-side comparison between a manual digitized raster and a Copernicus Emergency Management Service (CEMS) raster.

## Key Features

1.  **IoU Calculation**:
    * Automatically binarizes both input rasters (threshold > 0).
    * Computes the **Intersection over Union (IoU)** score to quantify the spatial overlap accuracy.
    * Prints the IoU score to the console for immediate logging.

2.  **Difference Mapping**:
    * Generates a difference map by subtracting the binary arrays (`Image 1 - Image 2`).
    * **Blue**: Area exists only in the Manual Digitized Map (False Negative).
    * **Red**: Area exists only in the CEMS Map (False Positive).
    * **White**: Areas where both maps agree (Intersection or Background).

3.  **Visualization (Matplotlib)**:
    * Produces a high-resolution, 3-panel figure:
        * **Left**: Manual Digitized Map (Ground Truth) in Blue.
        * **Center**: CEMS Map (Prediction) in Green.
        * **Right**: The Difference Map with a custom legend and calculated IoU score in the title.
    * Includes geospatial context with longitude/latitude axes and shared y-axes.

## Usage

```python
plot_ground_truth(
    path1="path/to/manual_digitized.tif", 
    path2="path/to/cems_prediction.tif", 
    save_path="output/comparison_result.png"
)
