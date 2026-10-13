# Prediction evidence

This folder contains segmentation predictions produced by the trained YOLOv8n-seg model on eight reinforced-concrete inspection images outside the training workflow.

## Files

- `contact_sheet.jpg`: Overview of all eight prediction outputs.
- `new_image_1.jpg` to `new_image_4.jpg`: Predictions for inspection images 1–4.
- `new_image_6.jpg` to `new_image_9.jpg`: Predictions for inspection images 6–9.
- `annotation_example.png`: Example of a ground-truth annotation used during dataset preparation.
- `val_batch0_pred.jpg` to `val_batch2_pred.jpg`: Predictions on validation batches during training.

Image 5 was excluded because it was a duplicate.

## Interpretation

Blue segmentation masks identify areas predicted as exposed reinforcement. Blue rectangles indicate the corresponding predicted bounding boxes. The evidence includes a no-detection case (`new_image_1.jpg`) and detections under varied viewpoints, lighting conditions, and structural elements.

For quantitative validation results, see [`../curves/results.png`](../curves/results.png) and [`../curves/results.csv`](../curves/results.csv).
