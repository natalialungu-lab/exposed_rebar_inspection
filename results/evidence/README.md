# Prediction evidence

This folder contains segmentation predictions produced by the trained YOLOv8n-seg model on new reinforced-concrete inspection images.

- `new_image_4.jpg`: Prediction on a concrete column or wall area with local exposed reinforcement.
- `new_image_5.jpg`: Prediction on an overhead concrete element with exposed reinforcement.
- `new_image_8.jpg`: Prediction on a damaged concrete wall or column area.

Blue regions show the predicted segmentation masks. Blue rectangles show predicted bounding boxes. These images demonstrate model inference on images outside the training workflow.

For quantitative validation results, see [`../curves/results.png`](../curves/results.png) and [`../curves/results.csv`](../curves/results.csv).
