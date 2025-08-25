# Blood Cell Classification with Deep Learning

This project implements an automated image classification system to distinguish between three types of white blood cells:
- **Basophils** – granulocytes involved in allergic reactions
- **Eosinophils** – granulocytes that combat parasites and participate in allergic responses
- **Neutrophils** – the most abundant white blood cells, first responders to infection

The classification system uses **deep learning with PyTorch** and leverages **transfer learning from EfficientNet-B0**, enabling accurate recognition of blood cell types from microscopic images.

## Dataset
- **Source:** CellaVision / Barcelona dataset (Mendeley Data)
- **Total Images:** ~7,600 (RGB, 363×360 pixels)
- **Split:** 80% training (~6,100 images), 20% testing (~1,500 images)
- **Balanced Representation:** Each of the three cell types included

A smaller sample set (~500 images) is also included for quick experimentation.

```

### Model Architecture
- **Base Model**: EfficientNet-B0 (pre-trained on ImageNet)
- **Transfer Learning**: Frozen feature extraction layers with custom classifier
- **Output Layer**: 3-class classification with dropout regularization (p=0.4)
- **Framework**: PyTorch with torchvision transforms

### Key Techniques Used

1. **Transfer Learning**
   - Leverages pre-trained EfficientNet-B0 features
   - Frozen backbone with trainable classification head
   - Reduces training time and improves performance on small dataset

2. **Custom Dataset Implementation**
   - PyTorch Dataset class with lazy loading for memory efficiency
   - Automatic label extraction from filename patterns
   - Built-in train/test splitting functionality

3. **Data Preprocessing**
   - Image standardization and tensor conversion
   - Automatic cropping for uniform dimensions
   - Efficient batch loading with DataLoader

4. **Model Evaluation**
   - Confusion matrix analysis for per-class performance
   - Visual prediction examples with confidence scores
   - Classification accuracy metrics

Automated blood cell classification has significant applications in:

- **Clinical Diagnostics**: Rapid screening for blood disorders and infections
- **Laboratory Automation**: Reducing manual cell counting workload
- **Medical Education**: Training tools for hematology students
- **Research**: Large-scale blood sample analysis for studies
- **Telemedicine**: Remote diagnostic capabilities in underserved areas

The ability to accurately classify white blood cell types can assist in diagnosing conditions like leukemia, infections, allergic reactions, and immune system disorders. Deep learning models capable of accurately classifying basophils are also important as they are naturally rarer and dataset for specifically basophils are smaller than the other bloodcell types.

## Project Structure

```
├── image_classification_project.ipynb    # Main notebook with complete implementation
├── bloodcells_dataset/                   # Dataset directory
│   ├── basophil/                        # Basophil cell images
│   ├── eosinophil/                      # Eosinophil cell images  
│   ├── neutrophil/                      # Neutrophil cell images
│   └── test_data.npy                    # Preprocessed test data
├── bloodcells_dataset_mendeley/
│   ├── basophil/                        
│   ├── eosinophil/                       
│   ├── neutrophil/ 
├── predictions.npy                       # Model predictions output
└── README.md                            # Project documentation
```

## Implementation Highlights

- **Memory-Efficient Design**: Images loaded on-demand to prevent CUDA memory issues
- **Robust Data Handling**: Automatic filename-based labeling with error checking
- **Visualization Tools**: Built-in functions for displaying sample images and predictions
- **Modular Architecture**: Clean separation between data loading, model definition, and evaluation

## Getting Started

1. **Requirements**: PyTorch, torchvision, scikit-learn, matplotlib, PIL, numpy
2. **Dataset**: Download the [mendeley dataset](https://doi.org/10.17632/snkd93bnjr.1) (PBC_dataset_normal_DIB.zip), unzip it, and move it into the project directory.
3. **Training**: Run the Jupyter notebook cells sequentially for data loading, model training, and evaluation
4. **Evaluation**: View confusion matrices and sample predictions to assess model performance
```

## Reference

Acevedo, A., Merino, A., Alférez, S., Molina, Á., Boldú, L., & Rodellar, J. (2020). A dataset of microscopic peripheral blood cell images for development of automatic recognition systems (Version 1) [Data set]. Mendeley Data. https://doi.org/10.17632/snkd93bnjr.1

