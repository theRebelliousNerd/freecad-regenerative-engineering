# 2.4. A Dimensional Guide to Custom Support Interfaces and Contact Points

The success of this custom support strategy hinges on precise dimensional control of the interface between the support structure and the part.

## Fin Spacing

The gap between the support fin and the main part is a critical dimension. The recommended spacing is between **0.5 mm and 1.0 mm**. This gap must be carefully calibrated. If it is too small, the fin will fuse to the part during printing, making it difficult or impossible to remove cleanly. If it is too large, the connecting sprues will be too long and may not provide adequate stability, or they may droop during printing. A gap of approximately two nozzle diameters (e.g., 0.8 mm) is often a good starting point.

## Interface Layers (The "Tabs")

The geometry of the connecting sprues or tabs determines the ease of removal. Their cross-section should be minimized to create a deliberate fracture point. A typical starting dimension for these tabs is a cross-section of one to two nozzle widths (e.g., a 0.4 mm x 0.8 mm rectangle). The shape can also be optimized; for instance, a cylindrical sprue will concentrate stress and snap more cleanly than a square one.

## Advanced Interface Techniques

For multi-material printers, an even more advanced technique can be employed. The main part can be printed in one material (e.g., PETG), while the support *interface layers*—the very top layers of the support structure that touch the part—can be printed in a dissimilar, non-adherent material (e.g., PLA). Because PETG and PLA do not bond well chemically, the part will rest on the support during printing but will separate from it perfectly afterward, leaving a flawless surface finish with zero scarring. This technique represents the pinnacle of support design, producing surfaces that are indistinguishable from non-supported top surfaces.
