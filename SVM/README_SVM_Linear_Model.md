# 📌 SVM Linear Model – Field Boundary Detection

## 🌾 Overview
This repository contains the implementation of a Support Vector Machine (SVM) classifier with a **Linear Kernel** used to perform binary segmentation of cropland fields from Sentinel-2 NDVI and TCI images. This model was used in the DAEN 690 Capstone Project titled *"Field Boundary Identification and Acreage Calculation using Sentinel-2 Imagery."*

## 🧠 Objective
Leverage an efficient and scalable pixel-based classifier for agricultural segmentation, optimized for rapid inference and minimal computational cost.

## 💡 Features Used
- **NDVI**: Normalized Difference Vegetation Index from 5 different dates.
- **TCI**: RGB bands (3 bands × 5 dates = 15).
- **Total Features**: 20 features per pixel.

## 🛠️ Workflow
1. **Data Preparation**:
   - Read and stack 5 NDVI `.tif` images and 5 TCI images.
   - Flatten images to form a 2D array (rows × features).
   - Load the ground truth mask and flatten to match.

2. **Training**:
   - Standardize features using `StandardScaler`.
   - Train using `LinearSVC` from `scikit-learn`.
   - Training Time: ~0.48 seconds

3. **Prediction & Evaluation**:
   - Inference Time: ~1.5 seconds on full AOI
   - Metrics: Pixel Accuracy = 91.03%, IoU = 71.54%, F1 = 0.83
   - Acreage Error = 18.27%

## 📊 Performance Summary
| Metric             | Value        |
|--------------------|--------------|
| Pixel Accuracy     | 91.03%       |
| IoU (Field Class)  | 71.54%       |
| F1-Score           | 0.83         |
| Acreage Error      | 18.27%       |

## 📂 Key Files
- `SVM_Linear_Model.ipynb` – Full training & testing code
- `NDVI_Stack_SVM.tif`, `TCI_Stack_SVM.tif` - created using clipped files folder under each date
- `ground_truth_mask.tif`
- `new_cdl_polygons.zip` - Test validation CDL ground truth shape file

## 🧰 Requirements
- Python 3.8+
- Libraries: `scikit-learn`, `rasterio`, `geopandas`, `numpy`, `matplotlib`

## 📎 Notes
- Best suited for **large-area predictions** and **fast deployment scenarios**.
- Works well for regional-scale mapping where accuracy and speed must be balanced.
