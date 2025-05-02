## Field Boundary Detection and Acreage Estimation using Random Forest

### Project Overview
This project focuses on detecting agricultural field boundaries and estimating field acreage using multi-temporal Sentinel-2 satellite imagery. A Random Forest classifier was trained on a custom-built feature matrix derived from NDVI and TCI images over multiple dates to accurately classify field and non-field pixels.

### Dataset Information
●	Satellite Imagery: Sentinel-2 Cloud-Optimized GeoTIFFs (Tile ID: 17TLJ)

●	Ground Truth Data: Manually digitized field boundaries within Huron County, Michigan (81 fields labeled)

●	Validation Data: USDA Cropland Data Layer (CDL)

### Preprocessing Steps
●	Selected Sentinel-2 images with <10% cloud cover and sun elevation between 50°–65°

●	Computed NDVI and extracted TCI (RGB bands) for five dates

●	Created a 20-feature matrix (5 NDVI + 15 TCI) per pixel

●	Generated binary masks for field vs background using QGIS annotations

### Model Details
●	Model Used: Random Forest Classifier

●	Feature Matrix: (#pixels, 20 features)

●	Training Labels: 1 = Field, 0 = Background

### Training and Validation Results
●	Training Time: 36.74 seconds

●	Prediction Time on Validation Set: 0.3542 seconds

●	Validation Accuracy: 97.00%

●	IoU (Field): 99.20%

●	F1-Score (Field Class): 0.98

●	Memory Usage: 606.19 MB

### Confusion Matrix
	Predicted Non-field	Predicted Field
Actual Non-field	7038	522
Actual Field	387	22,361
Acreage Estimation
●	Predicted Acreage: 311,670.97 acres

●	Ground Truth Acreage: 303,863.44 acres

●	Acreage Error: 7,807.53 acres (2.57% error)

### Key Findings
●	High pixel-wise classification performance with minimal acreage error.

●	Fast training and prediction times make the model suitable for real-time agricultural monitoring.

●	The multi-temporal feature approach significantly improves segmentation accuracy.

### Repository Structure
●	data/: Contains Sentinel-2 imagery and ground truth files

●	notebooks/: Jupyter notebooks for data preprocessing, training, and evaluation

●	models/: Trained Random Forest model files

●	outputs/: Visualizations and prediction results

### Requirements
●	Python 3.8+

●	rasterio

●	numpy

●	geopandas

●	scikit-learn

●	matplotlib

### Install all dependencies using:
pip install -r requirements.txt

### How to Run
1.	Load Sentinel-2 imagery and ground truth masks.

2.	Preprocess the imagery (NDVI/TCI calculation and stacking).

3.	Train the Random Forest model using the feature matrix.

4.	Predict field boundaries on the validation AOI.

5.	Evaluate the model and generate acreage estimates.

### Credits
●	European Space Agency (ESA) for Sentinel-2 imagery

●	USDA Cropland Data Layer

●	George Mason University, DAEN Program



