# Fold 1 results

These are the saved held-out test metrics for site1 (119 images). They are not aggregated cross-validation results.

| Metric | YOLOv12 Nano | YOLOv12 Small |
|---|---:|---:|
| Precision | 0.6121153504 | 0.3539230177 |
| Recall | 0.3018508107 | 0.2964475527 |
| mAP@0.5 | 0.3369042109 | 0.3043020668 |
| mAP@0.5:0.95 | 0.2257197789 | 0.2179081857 |
| Parameters (approx.) | 2.58M | 9.24M |
| Inference time | 12.3 ms | 18.5 ms |

On this particular Fold 1 test split, Nano has higher aggregate precision, recall, mAP@0.5, and mAP@0.5:0.95 than Small. This single-site result does not establish that Nano is universally better.

Validation metrics recorded during training:

| Metric | YOLOv12 Nano | YOLOv12 Small |
|---|---:|---:|
| Precision | 0.66576 | 0.57473 |
| Recall | 0.39587 | 0.42725 |
| mAP@0.5 | 0.45393 | 0.42071 |
| mAP@0.5:0.95 | 0.32384 | 0.29946 |

The saved test results are reported from the evaluation outputs retained in the notebook. This repository does not include model checkpoint weights or full evaluation artifacts.
