# Explainable sequence-aware deep learning based decadal shoreline modelling in the Southern Baltic until 2050

This repository provides **detailed description** that demonstrates the structure, variables, and formatting required to replicate the shoreline-change forecasting framework presented in the associated research article. The example dataset is a **representative subset**.

---

## 📁 Files included

* `example_data.csv`
  A small, stratified sample of the full dataset, intended for methodological illustration and code reproducibility.

* `model_training_inference.ipynb`
  Complete jupyter notebook containing code for LSTM-RNN model training, inference and validation.
  
* `data_processing.ipynb`
  Complete jupyter notebook containing code for Landsat images processing, pan-sharpening, DSAS outputs handling, processing and creating final csv ready for model training.
  
* `lstm_encoder_model_2025.pt`
  LSTM_RNN pre-trained model.
  
* `scalar_2025.joblib`
  LSTM_RNN model weights.
---

## 📌 Data structure

Each row represents a **single shoreline transect** summarized over a defined time window and paired with environmental forcing statistics (waves and sea level).

---

## 🧭 Column descriptions

### Spatial and identification fields

* **region**
  Categorical identifier for the coastal region or study area to which the transect belongs. Used for regional aggregation and comparison.

* **transect_id**
  Unique identifier for each shoreline transect. Transects are fixed cross-shore lines along which shoreline position change is measured through time.

* **lon**
  Longitude of the transect reference point (decimal degrees, WGS84).

* **lat**
  Latitude of the transect reference point (decimal degrees, WGS84).

* **bearing_deg**
  Azimuth (degrees clockwise from north) indicating the seaward orientation of the transect.

---

### Temporal fields

* **start_date**
  Start date of the analysis window used to compute shoreline change and environmental statistics (ISO format: `YYYY-MM-DD`).

* **end_date**
  End date of the analysis window (ISO format: `YYYY-MM-DD`).

* **start_year**
  Calendar year corresponding to `start_date`.

* **end_year**
  Calendar year corresponding to `end_date`.

* **duration_yrs**
  Length of the analysis window in years, computed as the difference between `end_date` and `start_date`.

---

### Shoreline change metric

* **nsm** (Net Shoreline Movement)
  Net cross-shore displacement of the shoreline over the analysis window (meters). Positive values indicate shoreline accretion (seaward advance), while negative values indicate erosion (landward retreat).

---

### Wave climate statistics

Wave statistics are computed over the time window defined by `start_date` and `end_date`.

* **swh_mean**
  Mean significant wave height (meters).

* **swh_min**
  Minimum significant wave height (meters).

* **swh_max**
  Maximum significant wave height (meters).

* **swh_std**
  Standard deviation of significant wave height (meters).

* **swh_p10**
  10th percentile of significant wave height (meters).

* **swh_p50**
  50th percentile (median) of significant wave height (meters).

* **swh_p90**
  90th percentile of significant wave height (meters).

---

### Wave direction statistics

Wave direction is represented using trigonometric components to avoid angular discontinuities.

* **wd_sin_mean**
  Mean sine of wave direction over the analysis window.

* **wd_cos_mean**
  Mean cosine of wave direction over the analysis window.

* **wd_mean_deg**
  Mean wave direction in degrees (0–360), derived from the sine and cosine components.

---

### Sea-level information

* **slr_mm**
  Mean sea-level rise contribution over the analysis window (millimeters), derived from regional or gridded sea-level data.

---

## 🔁 Intended use

* This example dataset is provided **for structural and methodological reference only**.
* It allows users to understand the expected data schema and to adapt their own shoreline, wave, and sea-level datasets to replicate the modeling framework.
* The values in this file should **not** be used for scientific inference or comparison.

---

# Software and data availability statement

The data utilized in the study comes from multiple sources as follows: Landsat time-series satellite imagery data was obtained from https://earthexplorer.usgs.gov/ which is operated by United States Geological Survey. Hydrodynamic variables were obtained from European Centre for Medium-Range Weather Forecasts (ECMWF), accessible at https://www.ecmwf.int/en/forecasts/datasets. While, mean sea level data including climatic forcing datasets were obtained from https://cds.climate.copernicus.eu/datasets/sis-water-level-change-timeseries-cmip6?tab=overview which is operated by Copernicus EU. The software DSAS used to calculate NSM rates can be downloaded from https://www.usgs.gov/centers/whcmsc/science/digital-shoreline-analysis-system-dsas and finally the software CMORPH used to validate the NSM rates can be obtained from https://github.com/ElsevierSoftwareX/SOFTX-D-25-00356.

