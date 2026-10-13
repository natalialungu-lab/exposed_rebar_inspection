# Error analysis

## Purpose

This document records qualitative errors observed during review of the exposed-rebar segmentation model. It identifies likely failure modes and actions for improving the training data and model performance.

## False positive: shadow or surface texture

A false positive can occur when a shadow, rust stain, crack, spalled-concrete edge, or strong surface texture is predicted as exposed reinforcement.

**Engineering consequence:** an image may be flagged for inspection even though visible exposed reinforcement is not present.

**Mitigation:** add more negative training examples containing shadows, staining, cracks, spalling, and rough concrete surfaces. A qualified engineer must review every prediction before any maintenance decision.

## False negative: small or obscured exposed reinforcement

A false negative can occur when actual exposed reinforcement is small, partly occluded by debris, poorly illuminated, photographed at an oblique angle, or shown at insufficient image resolution.

**Engineering consequence:** visible exposed reinforcement may not be highlighted by the model and could be missed during automated image screening.

**Mitigation:** add annotated examples with small, occluded, low-light, and oblique-view targets. Use higher-quality inspection photographs and validate the model on independent site images.

## Observed no-detection case: `new_image_1.jpg`

The final model produced no exposed-reinforcement prediction for `new_image_1.jpg`, as shown in `results/evidence/new_image_1.jpg`. This image is recorded as a no-detection case. It should be classified as a confirmed false negative only if manual review of the original inspection photograph verifies that exposed reinforcement is genuinely visible.

Possible contributing factors include the wide camera view, low contrast between the concrete surface and the suspected defect, shadows, and a limited visible target area.

**Engineering consequence:** a no-detection result must not be interpreted as confirmation that the inspected element is defect-free. A qualified structural engineer must review the original image and, where necessary, conduct site verification.

**Mitigation:** add annotated training examples with wide views, low-contrast defects, shadows, and small exposed-reinforcement regions; then validate the revised model using independent site images.

## Interpretation and safe use

The model output is an inspection flag only. A positive prediction does not confirm corrosion severity, structural safety, or repair scope. Similarly, an absent prediction does not confirm that a concrete element is free from defects.

All outputs must be reviewed by a qualified structural engineer before they influence inspection records, safety assessment, maintenance prioritisation, or repair decisions.
