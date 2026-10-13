# Governance checklist

## Purpose and intended use

This project uses YOLOv8 instance segmentation to identify visible exposed reinforcement in photographs of reinforced-concrete elements.

The system is intended only as an inspection-support tool. It may help prioritise image review and document visible areas of potential exposed reinforcement. It must not determine structural safety, corrosion severity, repair scope, or compliance with design standards.

## Data source and rights

The training dataset was obtained from Roboflow Universe and is credited in the project documentation.

The dataset is used under the Creative Commons Attribution 4.0 International licence (CC BY 4.0). Any reuse, modification, or redistribution must preserve appropriate attribution to the original dataset author and provide a link to the licence:

https://creativecommons.org/licenses/by/4.0/

Only images licensed for this project’s stated use should be included in the repository or training workflow.

## Personal data and privacy

Inspection images can contain personal data or commercially sensitive information, including people, faces, vehicle registration plates, site addresses, company identifiers, drawings, or asset-location information.

Before uploading or processing real site images:
- Obtain permission from the asset owner or data controller.
- Remove, blur, or crop identifiable people, faces, vehicle plates, and sensitive site information where possible.
- Do not upload confidential client images to public repositories.
- Store production data in access-controlled systems with defined retention rules.

## Human oversight and accountability

A qualified structural engineer must review all model outputs before they influence an inspection report, safety assessment, maintenance priority, or repair decision.

The model produces visual predictions only. The responsible engineer remains accountable for:
- confirming the presence of exposed reinforcement;
- assessing the severity and structural relevance of observed deterioration;
- deciding whether further investigation, testing, or intervention is required.

## Technical limitations and risk controls

Known sources of error include shadows, low light, moisture, occlusion, unusual camera angles, surface texture, cracks, rust staining, and spalled concrete.

Risk controls:
- Treat detections as inspection flags, not final findings.
- Record image source, model version, date, and reviewer decision.
- Validate performance on representative independent site images before deployment.
- Monitor false positives and false negatives during use.
- Retrain or recalibrate the model when the data domain changes.

## Regulatory and professional context

The prototype does not replace applicable building regulations, inspection procedures, structural assessment standards, or professional judgement.

Any operational deployment must follow the organisation’s health-and-safety processes, data-protection obligations, contractual requirements, and applicable professional engineering responsibilities.
