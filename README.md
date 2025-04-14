# Prostate Gland Segmentation on MRI

This project focuses on segmenting the central gland (CG) from T2-weighted MRI images using a pre-trained 3D UNet model from the MONAI model zoo. The pipeline includes evaluation of the pre-trained model on a new dataset (PI-CAI D2) and subsequent fine-tuning to improve performance.

## Project Overview

The project consists of two main phases:
1. **Evaluation** of the pre-trained MONAI model on the D2 dataset
2. **Fine-tuning** the model to adapt to the new dataset

## Directory Structure

```
prostate-gland-segmentation-on-MRI/
├── data/
│   └── PI-CAI/
│       ├── cohort.csv           # Patient metadata with file paths
│       └── file_data/           # Per-patient folders with T2 and gland NIfTI files
├── models/
│   └── prostate_mri_anatomy/    # Pre-trained MONAI model bundle with configs and weights
├── notebooks/
│   ├── part1_prostate_gland_segmentation.ipynb
│   └── part2_finetuning_unet.ipynb
├── prostate-seg-env/            # Python virtual environment
├── README.md
└── requirements.txt             # Python dependencies (optional)
```

## Setup Instructions

1. **Clone the repository**
```bash
git clone https://github.com/venky348/prostate-gland-segmentation-on-MRI
cd prostate-gland-segmentation-on-MRI
```

2. **Create and activate a virtual environment**
```bash
python -m venv prostate-seg-env
source prostate-seg-env/bin/activate
```

3. **Install required packages**
```bash
pip install -r requirements.txt
```

4. **Place data and model files**
   - Data should be placed under `data/PI-CAI/file_data/` with the following structure:
     ```
     <patient_id>/
       ├── <patient_id>_t2w.nii.gz
       └── <patient_id>_gland.nii.gz
     ```
   - The MONAI bundle should be located in `models/prostate_mri_anatomy/`.

## Approach Summary

- Uses MONAI transforms for spatial and intensity preprocessing
- Evaluates model using Dice coefficient metric
- Performs sliding window inference for full-volume prediction
- Implements visualizations for both best- and worst-performing cases
- Supports model fine-tuning with DiceCELoss

## Notebooks

- `part1_prostate_gland_segmentation.ipynb` – Evaluates the model and analyzes predictions
- `part2_finetuning_unet.ipynb` – Fine-tunes the model on the D2 dataset

## Notes

- The original preprocessing steps defined in `inference.json` were evaluated, but manual preprocessing yielded significantly better results.
- Results, figures, and detailed analysis are presented in the Jupyter notebooks.

