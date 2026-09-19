# Exposed Rebar Inspection

YOLOv8 segmentation prototype for flagging visible exposed reinforcement in reinforced-concrete inspection images for qualified human review.

## Problem and success criterion

### AECO problem
Concrete cover loss can expose reinforcement and increase the risk of corrosion and durability deterioration. This prototype screens inspection photographs and flags suspected exposed rebar for qualified-engineer review.

### Success criterion
The system must identify likely visible exposed reinforcement in inspection images and provide a confidence score and segmentation mask. It is an inspection-support tool only: it does not diagnose structural safety, quantify section loss, or prescribe repairs.

## Dataset and class definition

- **Dataset:** [Insert Roboflow dataset link]
- **Split:** 80% training / 20% validation.
- **Class:** `exposed_rebar`.
- **Positive definition:** A reinforcing steel bar visibly exposed because the concrete cover is absent or broken.
- **Excluded cases:** Cracks, rust staining without visible steel, spalled concrete without distinct reinforcement, shadows, wire mesh, pipes, and other metal objects.
- Full labelling rules: [docs/class_definition.md](docs/class_definition.md)

## Model and training configuration

- **Framework:** Ultralytics YOLOv8 segmentation.
- **Model:** [Insert model, e.g. YOLOv8n-seg].
- **Epochs:** 30.
- **Image size:** [Insert image size].
- **Batch size:** [Insert batch size].
- **Dataset version:** [Insert Roboflow version/link].
- **Ultralytics version:** [Insert version].

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
5. For inference on new images, open [baseline inference notebook](notebooks/baseline_inference.ipynb) and run all cells.

## Reproducibility proof

- **Last successful run:** [Insert date and time].
- **Hardware:** [Insert GPU or CPU].
- **Expected runtime:** [Insert range].
- **Training parameters:** 30 epochs; batch size [insert]; image size [insert].
- **Outputs:** validation metrics table and saved training curves.
- If a GPU is unavailable, a short verification run may be completed and the trained weights loaded for inference; this must be stated clearly.

## Repository contents

- [Notebooks](notebooks/) — baseline inference and training/evaluation.
- [Class definitions](docs/class_definition.md) — target class and annotation rules.
- [Error analysis](docs/error_analysis.md) — qualitative failure analysis and data-improvement actions.
- [Governance checklist](docs/governance_checklist.md) — privacy, limitations, and risk controls.
- [Training curves](results/curves/) — training and validation evidence.
- [Evidence pack](results/evidence/) — annotations and prediction examples.
- [Reports](reports/) — final slides and mini report.
- **Model weights:** [Insert download link to `best.pt`].

## Limitations and responsible use

Predictions must be reviewed by a qualified engineer. The model can confuse exposed reinforcement with cracks, shadows, rust staining, surface texture, and spalled concrete; it can also miss small, occluded, low-light, or unusual-viewpoint targets. A detection is an inspection flag, not a structural diagnosis or repair decision.

## Deliverables

- [Slides PDF](reports/slides.pdf)
- [Mini report PDF](reports/mini_report.pdf)
