# 🌍 Satellite Image Field Boundary Identification and Field Acreage Calculation (FBI & FAC)

## 📌 Project Overview

This capstone project, conducted in collaboration with **George Mason University CATSR** and **AgGenius Inc.**, applies **Computer Vision and Machine Learning** to detect agricultural **field boundaries** and calculate **field-level acreage** using multi-temporal **Sentinel-2 imagery**.

The primary goal is to build scalable models that can support precision agriculture, improve crop monitoring, and serve as a prototype for integrating satellite-based field detection into drone-based workflows.

## 🎯 Objectives

1. Automatically delineate agricultural field boundaries from satellite imagery.
2. Accurately compute field acreage based on detected boundaries.
3. Evaluate and compare multiple ML/DL models to find the best fit for different use cases (speed vs. accuracy).

## 🛰️ Dataset & Sources

- **Sentinel-2 Level-2A Cloud-Optimized GeoTIFFs (COGs)** via AWS Open Data Registry  
  🌐 https://registry.opendata.aws/sentinel-2-l2a-cogs/
- **USDA Cropland Data Layer (CDL)** for ground truth labels
- **Area of Interest**: Huron County, Michigan

## 🤝 Sponsor

- **Center for Air Transportation Systems Research (CATSR)**, George Mason University
- **Partner**: AgGenius Inc.

## 🛠️ Tools & Technologies

- Sentinel-2 imagery (NDVI, RGB/TCI bands)
- Python (scikit-learn, PyTorch, Rasterio, GeoPandas, NumPy)
- QGIS for ground-truth visualization and AOI processing
