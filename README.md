# SAE - Nutrition Cambodia

This project implements Small Area Estimation (SAE) for nutrition indicator in Cambodia, following the methodology of Van der Weide et al. (2022). The workflow includes data preparation, covariate selection, spatial diagnostics, model estimation, and prediction.

## Main Files

- [1-NIS-preprocessing.ipynb](1-NIS-preprocessing.ipynb):  
  Pre-processes NIS data for further analysis.

- [2-MPI-NIS.ipynb](2-MPI-NIS.ipynb):  
  Constructs MPI for NIS data for further analysis.

- [3-DHS-NIS-complete-SAE.ipynb](0-DHS-NIS-complete-SAE.ipynb):  
  Loads and merges DHS and NIS data, attaches geometries, and exports cleaned shapefiles for further analysis.

- [4-Covariates-Selection-SAE.ipynb](1-Covariates-Selection-SAE.ipynb):  
  Prepares georeferenced DHS data, processes geospatial covariates, applies urban masking, merges datasets, handles missing values, explores the target variable, and performs Lasso-based covariate selection. Exports the final dataset for modeling.

- [5-SAE-SEM.ipynb](2-SAE-SEM.ipynb):  
  Loads the processed data, fits OLS and Spatial Error Models (SEM), performs spatial diagnostics (Moran's I), predicts the target variable at the village level, and runs Monte Carlo simulations for uncertainty estimation.

- [functions.py](functions.py):  
  Contains utility functions for geospatial processing, raster manipulation, data transformation, missing value handling, plotting, and other helper routines used throughout the notebooks.

- [SAE-procedure.docx](SAE-procedure.docx):  
  Documentation of the SAE methodology and workflow.

## Data Folders

- `data/underlying/`:  
  Contains the main shapefiles for NIS and DHS data, as well as intermediate and processed geospatial data.

- `output/`:  
  Stores output shapefiles, merged datasets, and prediction results.

- `temp_files/`:  
  Temporary files, intermediate results, and reports.

## Workflow

1. **NIS Data Preparation:**  
   - Run [1-NIS-preprocessing.ipynb](1-NIS-preprocessing.ipynb) to prepare NIS data.

2. **NIS-based MPI Preparation:**  
   - Run [2-MPI-NIS.ipynb](2-MPI-NIS.ipynb) to prepare NIS-based MPI data.

3. **DHS and NIS Data Preparation:**  
   - Run [3-DHS-NIS-complete-SAE.ipynb](3-DHS-NIS-complete-SAE.ipynb) to prepare and export cleaned NIS and DHS shapefiles.

4. **Covariate Selection:**  
   - Use [4-Covariates-Selection-SAE.ipynb](4-Covariates-Selection-SAE.ipynb) to process covariates, handle missing data, and select features with Lasso.

5. **Modeling and Prediction:**  
   - Run [5-SAE-SEM.ipynb](5-SAE-SEM.ipynb) to fit OLS/SEM models, perform diagnostics, and generate predictions with uncertainty intervals.

## Requirements

- Python 3.x
- Jupyter Notebook
- geopandas, pandas, numpy, matplotlib, seaborn
- scikit-learn, scikit-gstat, rasterio, PyPDF2, fiona, shapely
- pysal, libpysal, esda, spreg

Install dependencies with:

```sh
pip install geopandas pandas numpy matplotlib seaborn scikit-learn scikit-gstat rasterio PyPDF2 fiona shapely pysal libpysal esda spreg
```

## Notes

- All file paths are set for Windows and may need adjustment for other environments.
- Intermediate and output files are saved in the `data/`, `output/`, and `temp_files/` directories.
- For details on the methodology, see [SAE-procedure.docx](SAE-procedure.docx).