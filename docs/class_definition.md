# Class Definition Contract

## Project purpose
Detect visible exposed reinforcement bars in photographs of general reinforced-concrete elements and flag images for human concrete-condition inspection.

## Class name
`exposed_rebar`

## Positive definition
A reinforcing steel bar visibly exposed where the concrete cover is absent or broken.

## Boundary cases
Do not label cracks, including cracks parallel to reinforcement or cracks with rust staining, unless a distinct visible steel bar can be seen.

Do not label rust stains without visible steel, spalled concrete without visible reinforcement, wire mesh, pipes, or other metal objects.

Label partially visible reinforcement only when it is clearly identifiable as rebar.

## Mask rule
Annotate the visible pixels of each exposed reinforcement region. Exclude surrounding concrete, voids, rust stains, and shadows. Do not label cracks unless visible reinforcement steel is clearly present.

## Minimum size
20 x 20 pixels in the original image. Do not label smaller or unclear objects.

## Decision it feeds
Flag the image for human concrete-condition inspection by a qualified engineer.

## Miss versus false alarm
A false negative is approximately three times more costly than a false positive because an image containing exposed reinforcement may not be flagged for review. A false positive mainly creates additional human review.

## Limitation
The model detects a visible feature only. It does not assess corrosion severity, loss of reinforcement section, concrete strength, structural capacity, or repair urgency.
