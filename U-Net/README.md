# 📌 U-Net Model – Field Boundary Segmentation

## 🌾 Overview
This directory contains the implementation and output of the U-Net deep learning model used for segmenting agricultural field boundaries using multi-temporal NDVI imagery. This model was developed as part of the DAEN 690 Capstone Project at George Mason University.

## 🎯 Objective
To extract precise binary field boundaries (field vs background) from Sentinel-2 imagery using semantic segmentation with a U-Net architecture.

## 🧠 Input Features
- Multi-date NDVI stack from Sentinel-2
- 5 NDVI bands (May to September 2019)
- Input patch size: 256×256
- Ground truth: Binary masks from CDL crop polygon shapefile

## 🛠️ Workflow
1. **Preprocessing**:
   - Clipped NDVI bands to AOI using shapefile
   - Stacked NDVI into a 5-channel raster
   - Generated 256×256 patches with overlap
   - Created binary masks from ground truth polygons

2. **Model Training**:
   - Model: Custom U-Net using PyTorch
   - Loss: Binary Cross Entropy
   - Optimizer: Adam (lr = 1e-4)
   - Epochs: 50, Batch Size: 8
   - Training Time: **~7.3 seconds**
   - Device: NVIDIA RTX 4060 Ti (CUDA)

3. **Inference**:
   - Performed on unseen AOI
   - Output: Full-scale binary field mask (`predicted_mask.tif`)
   - Visualization overlay generated for comparison

## 📊 Performance (Test AOI)
- **IoU (Field)**: 66.35%
- **Pixel Accuracy**: 87.13%
- **F1-Score**: 0.80
- **Acreage Error**: 18.45%
- **Inference Time**: ~6.7 sec (Bigger AOI)

## 📂 Folder Contents
- `UNet_Model.ipynb` – Training & inference notebook
- `Small_AOI_Ndvi_Multidate_Stack.tif` – NDVI stack for input
- `AOI_Ndvi_multidate_stack.tif` – Bigger AOI NDVI stack for model testing
- `AOI_Huron_24_03.zip` - Bigger AOI region shape file for model testing
- `clipped_geopro.zip` - Training model ground truth shape file
- `new_cdl_polygons.zip` - Test validation CDL ground truth shape file

## 🧰 Dependencies
- Python 3.8+
- torch, torchvision, rasterio, geopandas, matplotlib, numpy

## 📝 Notes
- Model only uses NDVI, no TCI included
- Designed for binary segmentation, not multi-class
- Effective for high-resolution spatial boundary detection

