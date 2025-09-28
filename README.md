# 🌍 GEOS PM2.5 Bias Correction & Downscaling Pipeline

This repository contains a Jupyter Notebook (`Downscaling_v1_4.ipynb`) that:
- Downloads **GEOS-FP forecast data** (hourly meteorology + 3-hour aerosol fields)
- Applies **bias correction** using pre-trained DNN models
- Performs **downscaling** from ~25 km to 5 km resolution
- Generates **visualizations** of PM2.5 fields

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone [https://github.com/<your-username>/<repo-name>.git](https://github.com/alqamahsayeed12/AQ_Downscaling.git)
cd AQ_Downscaling
