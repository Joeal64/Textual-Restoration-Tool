# Textual-Restoration-Tool
This will restore text

## Joeal’s bleed-through notebooks

- [Classification](joeal_notebooks/Bleedthrough_Classification.ipynb) detects candidate marks using histogram thresholds, edges and connected regions implemented with NumPy.
- [Restoration](joeal_notebooks/Bleedthrough_Restoration.ipynb) applies background normalisation, Otsu thresholding and Canny edge gating.

Open either notebook and run all cells with NumPy, OpenCV and Matplotlib installed. Both start with the bundled H-DIBCO H08 scan. Set `IMAGE_PATH` to try another image. The restoration notebook saves a PNG beside the input.
