# Notebook review notes

The repository notebook is a prepared copy of the cleaned YOLOv12 training/evaluation notebook. It has not been executed during packaging.

## Corrections made
- Marked earlier split-planning cells as historical/superseded so that the final manifest workflow is clear.
- Cleared a stale pre-training audit output that displayed YOLOv8 paths/configuration even though the source cell defines the YOLOv12 experiment.
- Removed an off-by-one error in the displayed best epoch; the saved CSV epoch value is already 1-based.
- Updated the checkpoint verification cell to check both the direct run-folder and `weights/` locations. Its old output was cleared because it falsely reported the Nano checkpoint as missing.

## Methodology item to verify before claiming exact protocol reproduction
The canonical manifest code builds a sparse class matrix by adding one entry per annotation. Sparse-matrix construction can sum duplicate entries when one image contains multiple instances of the same class. Confirm whether the official splitter expects a binary class-presence indicator per image; if so, collapse duplicate image/class entries to 1, regenerate all fold manifests, and retrain/evaluate the folds before treating results as produced under that corrected protocol.

## Runtime outputs
Notebook outputs are retained for traceability except for the stale/incorrect outputs described above. Since the notebook was not re-run during packaging, treat its outputs as records of the prior Colab run, not proof that every cell will run successfully in a fresh runtime.
