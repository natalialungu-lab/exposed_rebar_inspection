
# Training and validation curves

This folder contains quantitative results from the final YOLOv8n-seg training run (30 epochs).

## Files

- [results.png](results.png): Training and validation curves, including losses, precision, recall, and mAP across epochs.
- [results.csv](results.csv): Epoch-by-epoch numerical metrics exported by Ultralytics.

## Key validation results

| Metric | Bounding boxes | Segmentation masks |
|---|---:|---:|
| Precision | 0.805 | 0.808 |
| Recall | 0.703 | 0.717 |
| mAP50 | 0.772 | 0.762 |
| mAP50-95 | 0.529 | 0.470 |

The segmentation-mask metrics are the primary results because the model is trained for instance segmentation. The lower mAP50-95 indicates that predicted mask boundaries are less accurate at strict overlap thresholds.

These results support image screening only. The masks must not be used to calculate damaged area, steel loss, repair quantities, corrosion severity, or structural capacity.
