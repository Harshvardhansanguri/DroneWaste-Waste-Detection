# Experimental protocol and implementation notes

## Dataset inventory
The source dataset contains 4,993 images, 5,135 object annotations, and 20 categories. The recorded audit found 3,822 images without annotations (background/empty images). The data cover 17 sites.

## Site-wise evaluation design
The intended protocol is 17-fold leave-one-site-out evaluation: one entire site is held out for testing in each fold. The remaining 16 sites are divided into training and validation data, with a 10% validation fraction and seed 1337. The notebook creates manifests for all 17 folds.

## What has actually been run
Only Fold 1 has been trained and evaluated. Fold 1 holds out site1 and contains 4,386 training images, 488 validation images, and 119 test images. Do not claim that full 17-fold model evaluation has been completed.

## Reproducibility environment
The recorded training runs used Google Colab, a Tesla T4 GPU, Ultralytics 8.4.178, 50 epochs, image size 640, batch size 8, 2 workers, seed 1337, and early stopping patience 15. The notebook retains an earlier one-epoch YOLOv8 pipeline smoke test, explicitly labelled as a historical diagnostic rather than part of the YOLOv12 comparison.

## Further work
Train and evaluate the remaining 16 folds before presenting full cross-validation metrics. Confirm that iterative multilabel stratification uses binary class-presence-per-image labels, as expected for multilabel stratification. If the split-generation implementation is changed, regenerate manifests and retrain models so that reported results correspond to the final manifests.
