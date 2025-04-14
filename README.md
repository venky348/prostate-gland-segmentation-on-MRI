# Prostate Gland Segmentation on MRI using MONAI

This project implements prostate gland segmentation on T2-weighted MRI scans using a pre-trained 3D UNet model from the MONAI Model Zoo. The objective is to evaluate and fine-tune the model on the PI-CAI dataset.

---

##  Project Structure

```
prostate-gland-segmentation-on-MRI/
├── data/
│   └── PI-CAI/
│       ├── cohort.csv
│       └── file_data/               # Individual patient NIfTI volumes
├── models/
│   └── prostate_mri_anatomy/        # Pre-trained MONAI bundle
├── notebooks/
│   ├── part1_evaluation.ipynb       # Evaluate pre-trained model
│   └── part2_finetuning.ipynb       # Fine-tune on new data
├── README.md
└── requirements.txt
```

---

## Model Details

- **Architecture**: 3D UNet
- **Source**: MONAI Model Zoo
- **Target**: Segment the central gland (CG) from T2-weighted MRI
- **Preprocessing**: Resized to (96, 96, 96), intensity scaled, single-channel T2

---

## Data

- **Dataset**: PI-CAI (Prostate Imaging: Cancer AI)
- **Download**: [PI-CAI Dataset - Onedrive](https://indiana-my.sharepoint.com/personal/rshirad_iu_edu/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Frshirad%5Fiu%5Fedu%2FDocuments%2Fdata%2FPI%2DCAI&ga=1)
- The dataset includes T2-weighted MRI and gland annotations.
- `cohort.csv` contains metadata and paths to each patient scan and mask.

> **Note**: The dataset is not uploaded to this repository due to its size (>100MB). Please download and place it in `data/PI-CAI/`.

---

## Pre-trained Model

- **Model**: Prostate MRI Anatomy Segmentation
- **Download**: [MONAI Model Zoo](https://monai.io/model-zoo.html)
- Place it under: `models/prostate_mri_anatomy/`

> **Note**: The model bundle is not included in the repository due to size limits.

---

## Environment Setup

1. **Create and activate environment**
   ```bash
   conda create -n prostate-seg-env python=3.10
   conda activate prostate-seg-env
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **(Optional) Generate requirements.txt**
   ```bash
   pip freeze > requirements.txt
   ```

---

## Code Workflow

- **Part 1**: Load and evaluate the pre-trained MONAI model on the D2 dataset.
- **Part 2**: Fine-tune the model using Dice + CrossEntropy loss and observe improvement.
- Visualizations and Dice metrics are used to compare results and understand error cases.

---

## Results

The results (Dice scores, visualizations of predictions) are shown in the Jupyter notebooks. Best and worst-performing patients are visualized to analyze model performance.

