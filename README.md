# DesertGridResilience

This repository contains the dataset and code for the paper **"Novel Multi-Agent PINNs-GANs Framework for Desert Grid Resilience: A Saudi Vision 2030 Solution."**

## 📊 Dataset Description

Each CSV contains normalized hourly data:

- `timestamp`: Date and time
- `temperature`: Normalized °C
- `wind_speed`: Normalized km/h
- `dust_levels`: Normalized mg/m³
- `power_demand`: Normalized kWh

### Regions
- Taif, Riyadh, NEOM, Al-Jouf, Mojave (8760 hours each)
- New York (4380 hours urban simulation)

Weather data is based on Copernicus ERA5 approximations and synthetic modeling.

## 🧠 Code
- `generate_data.py`: Simulates dust and demand
- `preprocess_data.py`: Cleans and normalizes raw data

## 📝 License
- Code: MIT
- Data: CC BY 4.0
