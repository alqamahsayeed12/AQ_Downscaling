![Python](https://img.shields.io/badge/python-3.11-blue.svg)
![Conda](https://img.shields.io/badge/conda-environment-green.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![Keras](https://img.shields.io/badge/Keras-3.x-red.svg)

# PM2.5 Bias Correction & Downscaling

This repository contains a Jupyter Notebook (`Downscaling_v1_4.ipynb`) that:
- Downloads **GEOS-FP forecast data** (hourly meteorology + 3-hour aerosol fields)
- Applies **bias correction** using pre-trained DNN models
- Performs **downscaling** from ~25 km to 5 km resolution
- Generates **visualizations** of PM2.5 fields

---

## Getting Started

### 1. Clone the Repository
```bash
git clone [https://github.com/<your-username>/<repo-name>.git](https://github.com/alqamahsayeed12/AQ_Downscaling.git)
cd AQ_Downscaling


