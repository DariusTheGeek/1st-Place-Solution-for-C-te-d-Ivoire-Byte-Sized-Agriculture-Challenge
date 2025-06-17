# 🌾 Côte d'Ivoire Byte-Sized Agriculture Challenge 1st Place Solution

A high-performance agricultural land classification solution using Sentinel-2 satellite imagery, combining deep learning with gradient boosting for multi-temporal crop type identification in Côte d'Ivoire.

## 📊 Performance Metrics

- **Public LB Score**: 0.973978144  
- **Private LB Score**: 0.975995377

## 🔍 Overview

This solution addresses the Côte d'Ivoire Byte-Sized Agriculture Challenge, requiring classification of agricultural land use patterns using 12-band Sentinel-2 satellite imagery across 12 months. The approach combines ConvNeXt deep learning architecture with LightGBM ensemble methods, optimized for multi-temporal agricultural monitoring.

## 🏗️ Architecture

The solution architecture follows this pipeline:


## 🛠️ Setup Instructions

### Hardware Requirements

- Colab Pro: A100 40GB GPU High RAM option

## 🧠 Model Details

### Model Architecture

- **Primary Model**: LightGBM ensemble  
- **Secondary Model**: ConvNeXt-Small with multi-modal fusion  
- **Input**: 144-channel images (12 bands × 12 months)  
- **Classes**: 3 agricultural land use categories  
- **Backbone**: ConvNeXt pre-trained on ImageNet  

### Feature Engineering Pipeline

- **Spectral Band Statistics**: 8 statistical measures × 12 bands × 12 months = 1,152 features  
- **Vegetation Indices**: 101+ indices (NDVI, EVI, SAVI, etc.) using spyndex library  
- **Temporal Features**: Month-wise aggregations and seasonal patterns  
- **Metadata Features**: Geometric properties and data quality indicators  

### Configuration

**Key training parameters:**

- Image Size: 64×64 pixels (resized from original)  
- Batch Size: 32 (adjusted for GPU memory)  
- Learning Rate: 1e-4 with cosine annealing  
- Epochs: 53 (with early stopping)  
- Validation: 15-fold stratified cross-validation  
- Augmentations: Rotation, flip, brightness adjustment  

## 🔬 Feature Engineering Details

### Spectral Analysis

- **Band Statistics**: Mean, median, min, max, std, skewness, kurtosis, percentiles  
- **Temporal Aggregation**: Month-wise and seasonal pattern extraction  
- **Normalization**: MinMax scaling with outlier handling  

### Vegetation Indices

Key indices computed using `spyndex` library:

- NDVI: Normalized Difference Vegetation Index  
- EVI: Enhanced Vegetation Index  
- SAVI: Soil-Adjusted Vegetation Index  
- NDWI: Normalized Difference Water Index  
- 101+ additional indices for comprehensive vegetation analysis  

## 📝 How to Reproduce

1. Upload `Brainiac_1stPlace_ByteAgriculture_Solution.ipynb` to **Colab Pro**  
2. Select **A100 40GB GPU** with **High RAM**  
3. Run all cells to generate the `final_submission` file
