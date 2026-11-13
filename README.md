# DroneWaste: Deep Learning-Based Waste Detection in Aerial Imagery

Capstone project investigating waste recognition in drone imagery using the **DroneWaste dataset** and **YOLOv12 Nano / YOLOv12 Small**.

## Team
- Harshvardhan Sanguri
- Vanshika Dubey
- Ansh Panwar

## Project overview
The workflow covers dataset auditing, COCO-to-YOLO annotation conversion, site-wise split construction, YOLOv12 training, and held-out-site evaluation.

## Dataset and references
The project uses the DroneWaste dataset described in Morandini et al., “DroneWaste dataset for waste recognition in drone imagery,” *Scientific Data* (2026). DOI: https://doi.org/10.1038/s41597-026-07970-1

- Official repository: https://github.com/lucamora/dronewaste
- Official training protocol: https://github.com/lucamora/dronewaste/blob/main/docs/train.md
- Official evaluation protocol: https://github.com/lucamora/dronewaste/blob/main/docs/eval.md

The dataset files are **not included** in this Git repository. Obtain them from the official source and follow the dataset's terms.

## Current experimental status
All 17 site-wise fold manifests have been generated. **Only Fold 1 has been trained and evaluated so far.** The results below are therefore Fold 1 results, not completed 17-fold cross-validation results.

| Model | Parameters (approx.) | Test precision | Test recall | Test mAP@0.5 | Test mAP@0.5:0.95 | Inference |
|---|---:|---:|---:|---:|---:|---:|
| YOLOv12 Nano | 2.58M | 61.21% | 30.19% | 33.69% | 22.57% | 12.3 ms |
| YOLOv12 Small | 9.24M | 35.39% | 29.64% | 30.43% | 21.79% | 18.5 ms |

The Fold 1 test set contains 119 images, including 75 annotated instances and 84 background images. These results are specific to the held-out site1 split and are not directly comparable to the paper's aggregate evaluation results.

## Repository layout
```text
.
├── README.md
├── .gitignore
├── notebooks/
│   └── 02_yolov12_training_and_evaluation.ipynb
├── docs/
│   ├── experimental_protocol.md
│   ├── notebook_review_notes.md
│   └── results.md
└── results/
    └── fold_01/
        └── comparison_metrics.json
```

## Reproducing the workflow
The notebook was developed for Google Colab with Google Drive mounted. It expects dataset and intermediate files under `/content/drive/MyDrive/DroneWaste` and temporary working files under `/content/dronewaste_work`. Update these paths when reproducing elsewhere.

Recorded YOLOv12 comparison settings: 50 epochs, image size 640, batch size 8, 2 workers, seed 1337, patience 15, and Tesla T4 GPU.

The notebook has not been re-executed as part of repository preparation. The stale YOLOv8 configuration output, best-epoch display, and Nano checkpoint-path check identified during review have been corrected or cleared. See `docs/notebook_review_notes.md` for remaining methodology caveats.

## Large files intentionally excluded
Dataset archives, generated images and labels, training run directories, and model checkpoint weights (`.pt`) are excluded from Git to keep the repository lightweight. Original data and trained checkpoints remain external to this repository.
