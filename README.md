![Python](https://img.shields.io/badge/python-3.11-blue.svg)
![Conda](https://img.shields.io/badge/conda-environment-green.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![Keras](https://img.shields.io/badge/Keras-3.x-red.svg)

# PM2.5 Bias Correction & Downscaling

This repository contains a Jupyter Notebook (`main_v1_4.ipynb`) that:
- Downloads **GEOS-FP forecast data** (hourly meteorology + 3-hour aerosol fields)
- Applies **bias correction** using pre-trained DNN models
- Performs **downscaling** from ~25 km to 5 km resolution
- Generates **visualizations** of PM2.5 fields

---

## Getting Started

### 1. Clone the Repository
```` bash 
git clone [https://github.com/alqamahsayeed12/AQ_Downscaling.git]
cd AQ_Downscaling
````

### 2. Create Conda Environment

This repository includes an downscaling_env.yml file for reproducibility.

```` bash 
conda env create -f downscaling_env.yml
conda activate tf213

````
### 3. Launch Jupyter Notebook
```` bash
jupyter notebook
````
---

## Directory Structure

The notebook automatically creates these folders:
````
IN_NetCDF/        # Raw input NetCDF files
Scalars/          # Scaling factors (max_min4.csv)
OUT_BC/           # Bias corrected NetCDF outputs
OUT_DS/           # Downscaled NetCDF outputs
Model/            # Pre-trained models (.h5)
PLOTS/            # Visualization outputs
````
---

## Usage Instructions

### 1. Run the Notebook
You’ll be prompted to enter:

- A date in YYYYMMDD format (must be within the last 28 days)

- Latitude/Longitude bounds

### 2. Recommended working domain:

Latitude: -11.25 to 28.5
Longitude: 91.8 to 141.6
If lat/lon arrays are not multiples of 40, they are trimmed.

### 3. Data Download
If no local input files are found, the notebook triggers the download function and downloads:

- 3-day forecst of 3-hour aerosol field (tavg3_2d_aer_Nx)

- 3-day forecast of 1-hour meteorology field (every 3rd file4 files for tavg1_2d_slv_Nx)

### 4. Bias Correction & Downscaling

- Applies DNN-based bias correction (BC_DNN_PM25)

- Downscales both GEOS and bias-corrected PM2.5 to ~5 km resolution

### 5. Visualization

Generates side-by-side maps saved in:

  - PLOTS/Day1/

  - PLOTS/Day2/

  - PLOTS/Day3/

---
## Example Outputs

  - Bias-corrected NetCDF → OUT_BC/v1_4_BC_YYYYMMDDHH.nc

  - Downscaled NetCDF → OUT_DS/v1_4_DS_YYYYMMDDHH.nc

  - Plots → PLOTS/DayX/v1_4_YYYYMMDD_HHMM.png

## Variables included:

  - GEOSPM25 – Raw GEOS PM2.5

  - BC_DNN_PM25 – Bias corrected PM2.5

  - DS_GEOSPM25 – Downscaled GEOS PM2.5

  - DS_BC_DNN_PM25 – Downscaled bias corrected PM2.5


---
## Quickstart Script

For convenience, a one-step setup script is included:
  - quickstart.sh

```
#!/usr/bin/env bash
# Quickstart script Downscaling

echo "Setting up environment..."

# Clone repo if not already present
if [ ! -d "AQ_downscaling" ]; then
  git clone https://github.com/alqamahsayeed12/AQ_Downscaling.git
fi
cd AQ_Downscaling

# Create and activate conda environment
conda env create -f downscaling_env.yml || conda env update -f downscaling_env.yml
conda activate tf213

# Launch Jupyter
echo "Environment ready. Launching Jupyter..."
jupyter notebook

```

### Run:

```
bash quickstart.sh
```
---
### Notes

- Only dates within the last 28 days are supported (GEOS-FP server limitation)

- If latitude/longitude grids are not multiples of 40, they are trimmed logically

- Pre-trained models must be in /Model/

### License

MIT License. Free to use and adapt with citation.

### Acknowledgments

NASA-SERVIR and SERVIR-South East Asia



