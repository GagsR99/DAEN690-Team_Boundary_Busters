# 📌 SVM RBF Model – Field Segmentation with Non-Linear Kernel

## 🌾 Overview
This directory includes the code and assets for training a Support Vector Machine (SVM) with a **Radial Basis Function (RBF)** kernel, used for pixel-wise segmentation of agricultural fields using Sentinel-2 NDVI and TCI images.

## 🧠 Objective
Improve prediction accuracy and boundary segmentation performance for small-to-medium AOIs with complex field structures.

## 💡 Features Used
- **NDVI**: 5 time periods
- **TCI**: 3 bands × 5 dates
- **Total**: 20 features per pixel

## 🛠️ Workflow
1. **Data Preparation**:
   - Stack multi-date NDVI and TCI bands
   - Create flattened input and ground truth masks
2. **Training**:
   - SVM with RBF kernel using `SVC(kernel='rbf')`
   - Training Time: ~334.60 seconds
3. **Prediction & Evaluation**:
   - Inference Time: ~17 minutes for large AOI
   - Pixel Accuracy = 85.37%
   - IoU = 69.5%
   - F1 = 0.82
   - Acreage Error = 8.20%

## 📊 Performance Summary
| Metric             | Value        |
|--------------------|--------------|
| Pixel Accuracy     | 85.37%       |
| IoU (Field Class)  | 69.50%       |
| F1-Score           | 0.82         |
| Acreage Error      | 8.20%        |

## 📂 Key Files
- `SVM_RBF_Model.ipynb` – End-to-end code
- `NDVI_Stack_SVM.tif`, `TCI_Stack_SVM.tif` - created using clipped files folder under each date
- `ground_truth_mask.tif`
- `new_cdl_polygons.zip` - Test validation CDL ground truth shape file

## 🧰 Requirements
- Python 3.8+
- Libraries: `scikit-learn`, `rasterio`, `geopandas`, `numpy`, `matplotlib`

## 📎 Notes
- Best suited for **small-scale or precision applications**.
- Provides better segmentation in complex regions but slower to scale.
