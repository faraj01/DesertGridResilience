# DesertGridResilience Dataset

This repository contains the datasets used in the manuscript *"AI-Driven MA-PINNs: Advancing Sustainable Power Demand Forecasting in Desert Smart Grids with Federated Learning and Cybersecurity"* by Hamzah Faraj, submitted to the *Alexandria Engineering Journal* on June 03, 2025.

## Dataset Overview
The dataset includes hourly measurements from six desert regions over one year (8760 hours, from 2024-01-01 to 2024-12-31), collected at 1 Hz and aggregated to hourly resolution. The regions are:
- **Taif (5 MW)**: 30% sandstorm noise.
- **Riyadh (10 MW)**: General desert conditions.
- **NEOM (10 GW)**: Low-gradient region with high dust (1 mg/m³).
- **Al-Jouf (1 MW)**: Small grid, focus on energy equity.
- **Tabuk (5 MW)**: 25% sandstorm noise at 40 km/h wind speed.
- **Mojave (50 GW)**: High temperatures (50°C) and dust (1–2 mg/m³).

### Variables
- `timestamp`: Date and time (YYYY-MM-DD HH:MM:SS).
- `temperature`: Temperature in °C (raw) or scaled (processed).
- `dust`: Dust level in mg/m³ (raw) or scaled (processed).
- `wind_speed`: Wind speed in km/h (raw) or scaled (processed).
- `demand`: Power demand in kWh (raw) or scaled (processed).
- `is_synthetic` (Tabuk only): Boolean flag indicating synthetic demand data due to simulated sandstorm noise.

### Data Sources
- Mojave solar data: National Renewable Energy Laboratory (NREL, 2023).
- Weather data: ERA5 Hourly Data on Single Levels (Copernicus Climate Change Service, 2023).
- Synthetic data: 20% of Tabuk’s demand data includes simulated sandstorm noise (Gaussian noise, \(\sigma = 0.25\)).

## Directory Structure
- `raw_data/`: Hourly data before preprocessing.
  - `raw_taif.csv`, `raw_riyadh.csv`, ..., `raw_mojave.csv`
- `processed_data/`: Hourly data after preprocessing.
  - `processed_taif.csv`, `processed_riyadh.csv`, ..., `processed_mojave.csv`
- `metadata/`: Documentation files.
  - `README.md` (this file).
  - `data_dictionary.md` (detailed variable descriptions).
- `scripts/`: Python scripts for preprocessing.
  - `generate_datasets.py`: Script to generate and preprocess the data (illustrative).

## Preprocessing Steps
1. **Sparse GPR**: Imputes 5% missing data using a Gaussian Process with 100 inducing points.
2. **Wavelet Denoising**: Applies Daubechies D4 wavelet (\(\lambda = 0.05\)) to reduce 15% noise.
3. **Robust Scaling**: Uses a robust scaler to handle outliers (scikit-learn’s `RobustScaler`).
