# 📌 Support Vector Machine (SVM) Models for Field Boundary Detection

## 🌾 Overview
This section includes two implementations of Support Vector Machine (SVM) classifiers for agricultural field segmentation using Sentinel-2 satellite imagery. Both models use pixel-wise classification based on multi-temporal NDVI and TCI features.

---

## 🔹 SVM with Linear Kernel

### 🎯 Objective
Build a high-speed, scalable model for detecting field boundaries across large regions.

### 💡 Features
- 5 NDVI bands from May–September
- 15 TCI bands (3 RGB bands × 5 dates)
- 20 features per pixel

### 🛠️ Training & Inference
- Normalization with StandardScaler
- Trained with `LinearSVC` from scikit-learn
- Training Time: ~0.48 seconds
- Inference Time: ~1.5 seconds on full AOI

### 📊 Performance
| Metric             | Value        |
|--------------------|--------------|
| Pixel Accuracy     | 91.03%       |
| IoU (Field Class)  | 71.54%       |
| F1-Score           | 0.83         |
| Acreage Error      | 18.27%       |

### 📂 Key Files
- `SVM_Linear_Model.ipynb`
- `NDVI_Stack_SVM.tif`, `TCI_Stack_SVM.tif` - created using clipped files folder under each date
- `ground_truth_mask.tif`
- `new_cdl_polygons.zip` - Test validation CDL ground truth shape file

---

## 🔹 SVM with RBF Kernel

### 🎯 Objective
Capture complex, non-linear boundaries for precision segmentation.

### 💡 Features
- 5 NDVI layers
- 15 TCI bands
- 20 features per pixel

### 🛠️ Training & Inference
- Uses `SVC(kernel='rbf')` from scikit-learn
- Training Time: ~334.60 seconds
- Inference Time: ~17 minutes on full AOI

### 📊 Performance
| Metric             | Value        |
|--------------------|--------------|
| Pixel Accuracy     | 85.37%       |
| IoU (Field Class)  | 69.50%       |
| F1-Score           | 0.82         |
| Acreage Error      | 8.20%        |

### 📂 Key Files
- `SVM_RBF_Model.ipynb`
- `NDVI_Stack_SVM.tif`, `TCI_Stack_SVM.tif` - created using clipped files folder under each date
- `ground_truth_mask.tif`
- `new_cdl_polygons.zip` - Test validation CDL ground truth shape file

---

## 🧰 Dependencies
- Python 3.8+
- scikit-learn, rasterio, geopandas, matplotlib, numpy

## 📝 Notes
- **Linear SVM**: Best for fast inference and large-scale deployments
- **RBF SVM**: Best for small-to-medium AOIs requiring precision segmentation
