# Exposed Rebar Inspection

YOLOv8 segmentation prototype for flagging visible exposed reinforcement in reinforced-concrete inspection images for qualified human review.

## Problem and success criterion

### AECO problem
Concrete cover loss can expose reinforcement and increase the risk of corrosion and durability deterioration. This prototype screens inspection photographs and flags suspected exposed rebar for qualified-engineer review.

### Success criterion
The system must identify likely visible exposed reinforcement in inspection images and provide a confidence score and segmentation mask. It is an inspection-support tool only: it does not diagnose structural safety, quantify section loss, or prescribe repairs.

## Dataset and class definition

- **Dataset:** https://universe.roboflow.com/rebar-exposure-and-spalling/rebar-exposure-qm02o/dataset/4
- **Split:** 1,547 training images and 168 validation images
- **Class:** `exposed_rebar`.
- **Positive definition:** A reinforcing steel bar visibly exposed because the concrete cover is absent or broken.
- **Excluded cases:** Cracks, rust staining without visible steel, spalled concrete without distinct reinforcement, shadows, wire mesh, pipes, and other metal objects.
- Full labelling rules: [docs/class_definition.md](docs/class_definition.md)

## Model and training configuration

- **Framework:** Ultralytics YOLOv8 segmentation.
- **Model:** YOLOv8n-seg (`yolov8n-seg.pt`).
- **Epochs:** 30.
- **Image size:** 640.
- **Batch size:** 8.
- **Device:** NVIDIA Tesla T4 GPU.
- **Random seed:** 42.
- **Training duration:** approximately 20 minutes.
- **Dataset version:** Roboflow `rebar-exposure-qm020`, version 4.

## Results summary

| Metric | Validation result |
|---|---:|
| Mask precision | 0.808 |
| Mask recall | 0.717 |
| Mask mAP50 | 0.762 |
| Mask mAP50-95 | 0.470 |

Key observations:
- The model detects clear exposed reinforcement meshes and bars in several concrete-damage contexts.
- Some masks are coarse and include adjacent spalled concrete.
- Errors include missed rebar in low-light or wide-view scenes and false alerts on cracks, shadows, and spalling.

## How to reproduce in Google Colab

1. Open [training and evaluation notebook](notebooks/training_evaluation.ipynb).
2. In Colab, select **Runtime > Change runtime type > T4 GPU**, if available.
3. Run all cells from top to bottom.
4. The notebook downloads the dataset, trains the model for 30 epochs, evaluates validation metrics, and saves plots.
5. For inference on new images, use the inference section at the end of the [training and evaluation notebook](notebooks/training_evaluation.ipynb), after the training and validation cells.

## Reproducibility proof

- **Last successful run:** 19 September 2026, approximately 17:00 CEST.
- **Hardware:** NVIDIA Tesla T4 GPU (14,913 MiB).
- **Expected runtime:** approximately 20 minutes for 30 epochs.
- **Training parameters:** 30 epochs; batch size 8; image size 640; random seed 42.
- **Outputs:** validation metrics table, `results.csv`, training curves, confusion matrices, labelled validation images, validation predictions, and `best.pt` weights.
- **Final run folder in Colab:** `/content/runs/exposed_rebar_30epochs/`.

## Repository contents

- [Notebooks](notebooks/) — baseline inference and training/evaluation.
- [Class definitions](docs/class_definition.md) — target class and annotation rules.
- [Training curves](results/curves/) — training and validation evidence.
- [Evidence pack](results/evidence/) — validation outputs and segmentation predictions on new inspection images.
- [Reports](reports/) — final slides and mini report.
- **Model weights:** [`best.pt`](models/best.pt) — trained YOLOv8n-seg checkpoint from the final 30-epoch run.

## Limitations and responsible use

Predictions must be reviewed by a qualified engineer. The model can confuse exposed reinforcement with cracks, shadows, rust staining, surface texture, and spalled concrete; it can also miss small, occluded, low-light, or unusual-viewpoint targets. A detection is an inspection flag, not a structural diagnosis or repair decision.

## Deliverables

- [Slides PDF](reports/Slides%20PDF.pdf)
- [Mini report PDF](reports/Mini%20report%20PDF.pdf)
