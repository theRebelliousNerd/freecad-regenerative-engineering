# Foundational Principles of Design for FDM Mass Production

The transition to FDM for mass production necessitates a mastery of foundational design principles that are intrinsically linked to the physics of the layer-by-layer fabrication process. These principles are not isolated rules but form an interconnected system where a single design choice can simultaneously influence print speed, structural integrity, visual quality, and the potential for automation. Adherence to these fundamentals is the primary determinant of success and economic viability at scale.

## 1.1. Wall Thickness and Structural Integrity

In the context of mass production, wall thickness is a primary consideration for ensuring part strength, reliability, and print quality. The guidelines differ significantly from both hobbyist printing and injection molding.

### The "Two-Perimeter" Rule

A non-negotiable standard for production-grade parts is a minimum wall thickness of 1 mm. This dimension is derived directly from the standard FDM nozzle diameter of 0.4 mm. A 1 mm wall allows the printer to lay down at least two concentric perimeters, or "shells," with a slight overlap (e.g., two 0.4 mm lines create a 0.8 mm wall, with side extrusion filling the remainder). A single-perimeter wall is structurally weak, prone to porosity, and susceptible to failure during handling or use. The two-perimeter standard ensures a solid, dimensionally stable, and watertight vertical surface, forming the baseline for any professional-grade component. Designers should conceptualize the fundamental unit of their design not as an infinitely variable solid, but as a construct built from these 0.4 mm "3D pixels".

### Avoiding Cavities and Thin Features

A common practice in injection molding is "coring out" or "shelling" a part to create a uniform, thin wall, thereby saving material and reducing cycle time. Applying this logic to FDM is a critical error. 3D printing does not suffer from the same constraints. Large, solid volumes are not a detriment; instead, they are efficiently filled with a low-density internal lattice structure, commonly referred to as infill (e.g., honeycomb, gyroid, or triangular patterns). This infill provides significant structural support with minimal material usage and print time.

Attempting to hollow out a part in CAD creates thin, unsupported walls that are inherently weak. During printing, these thin features are more susceptible to vibration and temperature fluctuations, leading to poor surface quality. Structurally, they create stress concentrations and are prone to delamination along the layer lines, effectively "unzipping" under load. The DFAM principle is therefore counterintuitive to those trained in DFM: to increase strength, add more volume. Designing thicker, "chunkier" parts that leverage the strength of infill results in a more robust and reliable product than one designed with thin, hollowed-out walls.
