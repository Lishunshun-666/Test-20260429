# Divergent shifts in vegetation moisture memory across global meteorological and soil-moisture pathways

## 1. System requirements
Operating system: Windows 64-bit
Python version: 3.11.11
Python distribution: Anaconda


## 2. Environment
The project was developed and tested in Python 3.11.11 using Anaconda on a 64-bit Windows system. The notebooks were tested in a Jupyter Notebook / JupyterLab environment.
All required Python packages and version numbers are listed in `requirements.txt`.
No non-standard hardware is required.


## 3. Installation guide
Install the required packages using:
pip install -r requirements.txt
Typical installation time on a "normal" desktop computer is approximately 5–10 minutes.


## 4. Demo data
The full analysis includes 64 repeated experiments based on:

2 relationship types: SMrz-SIF and SPEI-SIF
4 seasons: MAM, JJA, SON, and DJF
4 climate zones: Temperate, Tropical, Boreal, and Arid
2 output variables: Rmax and Ts

To keep the submission package lightweight and easy to evaluate, only a small representative subset of the data is included in this archive for demonstration purposes.
The demo subset includes one representative season-climate combination for each relationship type and output variable.
The same analysis workflow was applied to all other combinations.


## 5. Demo
The archive contains Jupyter notebooks corresponding to the main and supplementary figures, as well as notebooks for key analysis steps.

To run the demo:

Install the required packages listed in requirements.txt.
Open the notebook files in Jupyter Notebook or JupyterLab.
Make sure the demo data are placed in the correct folder.
Run the cells sequentially in the notebooks supported by the included demo data. 
Some preprocessing notebooks are provided to document the full workflow but require larger original datasets that are not included in this archive.
Expected output:

The notebooks generate representative analysis outputs and figures for the provided demo dataset. 
Outputs corresponding to the included demo files should be reproducible when the notebooks are run in order.

Expected run time for the demo on a "normal" desktop computer is approximately 10–30 minutes, depending on the notebook and dataset size.


## 6. Instructions for use
The code is organized by figure and key analysis step.

Included notebooks cover:

- Main figures
- Supplementary figures
- Key analytical procedures

To apply the workflow to your own data:

1. Prepare input data in the same format as the provided demo dataset.
2. Modify file paths if necessary.
3. Run the relevant notebooks in sequence.
4. Save the generated outputs and figures.


## 7. Key analysis scripts
- `Rmax_Ts.ipynb`: includes the main workflow for correlation-based analysis. 
In the first data-processing step, the notebook computes Spearman correlations between SIF and environmental anomaly time series across multiple timescales, and then identifies, for each grid cell, the maximum absolute correlation together with the corresponding optimal timescale and month. 
The SPEI–SIF case is presented here as an example, while the same procedure is used for the SMrz–SIF analysis. 
The code example shown in the notebook uses the 2001–2010 time window as a representative case, whereas the full analysis is repeated for 11 moving time windows from 2001–2010 to 2011–2020. 
For demonstration purposes, the archive includes only a partial subset of the required SPEI inputs (for example, the 01-timescale group with 12 monthly datasets), rather than the full 01–48 timescale collection used in the complete analysis. 
Therefore, the included demo data illustrate the preprocessing workflow but do not support full reproduction of the complete maximum-correlation selection step.

- `SMrz_timescale.ipynb`: performs preprocessing of monthly root-zone soil moisture (SMrz) data for the subsequent SIF–SMrz correlation analysis. 
The notebook merges the original monthly NetCDF files into a continuous time series, computes antecedent moving-average SMrz conditions across 1–48 month timescales, shifts each series by one month, and then separates the outputs by calendar month. 
The processed NetCDF files are used as inputs for the later pixel-wise Spearman correlation analysis. Because the raw SMrz input data required for this preprocessing step are large, they are not included in the submission archive. 
Therefore, this notebook is provided to document the preprocessing workflow, but it cannot be fully executed from the included files alone.


## 8. Reproducibility notes
The complete study involved repeated analyses across all combinations of relationship type, season, climate zone, and output variable. Only a representative subset of the data is included in this submission package for demonstration purposes. The same workflow was used for all analyses.


## 9. Main files
The submission package includes:

- `README.md`
- `requirements.txt`
- `Data Processing/`, containing key preprocessing and analysis notebooks together with representative input files
- `Figure/`, containing notebooks and representative files for main and supplementary figures
- Demo dataset files required for the included examples


## 10. License
This code is provided for academic, research, and non-commercial use only.
Please contact the authors for permission for other uses.


## 11. Code availability
The code is provided in the submission archive and is also publicly available at:
https://github.com/Lishunshun-666/Test-20260429


## 12. File structure
Code/
├── README.md
├── requirements.txt
├── Data Processing/
│   ├── Rmax_Ts.ipynb
│   ├── SMrz_timescale.ipynb
│   ├── SIF_HDmonth/
│   │   └── OCO2.SIF.selyear_2001-2020_selmonth01-12.nc
│   ├── SM_Monthly_Grouped/
│   │   └── SM_timescale1_mon01-12.nc
│   └── SPEI/
│       └── spei01_selyear_2001-2020_selmonth01-12.nc
├── Figure/
│   ├── Fig.1/
│   │   ├── Fig.1.ipynb
│   │   ├── final_mask_n2.tif
│   │   ├── time_scale_trend_analysis_Spring_full11.nc
│   │   └── max_correlation_trend_analysis_Spring_full11.nc
│   ├── Fig.2/
│   │   ├── Fig.2.ipynb
│   │   ├── Fig.2a/
│   │   │   ├── mean_area_proportion_[Season].csv
│   │   │   └── rate_of_change_in_proportion_[Season].csv
│   │   └── Fig.2b/
│   │       ├── SM/
│   │       │   ├── mean_area_proportion_Ts_[Season].csv
│   │       │   └── rate_of_change_in_proportion_Ts_[Season].csv
│   │       └── SPEI/
│   │           ├── mean_area_proportion_Ts_[Season].csv
│   │           └── rate_of_change_in_proportion_Ts_[Season].csv
│   ├── Fig.3/
│   │   ├── Fig.3.ipynb
│   │   ├── SMrz_Rd111.xlsx
│   │   ├── SMrz_Tsd111.xlsx
│   │   ├── SPEI_Rd111.xlsx
│   │   └── SPEI_Tsd111.xlsx
│   ├── Fig.4/
│   │   ├── Fig.4.ipynb
│   │   ├── All_variables_merged.nc
│   │   ├── 2011-2020_Spring_trend.nc
│   │   ├── significant_mask_p005_Spring_maxcorr.nc
│   │   ├── Arid.nc
│   │   ├── Boreal.nc
│   │   ├── Temperate.nc
│   │   └── Tropical.nc
│   ├── Fig.S1-S5/
│   │   └── Fig.S1-S5.ipynb
│   ├── Fig.S6-S7/
│   │   ├── Fig.S6-S7.ipynb
│   │   ├── final_mask_n2.tif
│   │   └── timescale_spei_float/
│   │       └── max_corr_2001-2010_to_2011-2020_[Season].nc
│   └── Fig.S8/
│       ├── Fig.S8.ipynb
│       ├── 01_SPEI/
│       │   └── [timescale]_[Season]/
│       │       ├── heatmap_matrix_*.csv
│       │       ├── global_id_*.nc
│       │       ├── overlap_count_*.nc
│       │       ├── global_cluster_summary_*.csv
│       │       ├── overlap_frequency_stats_*.csv
│       │       ├── per_window_stats_*.csv
│       │       └── connection_log_*.csv
│       └── 02_SM/
│           └── [timescale]_[Season]/
│               └── heatmap_matrix_*.csv