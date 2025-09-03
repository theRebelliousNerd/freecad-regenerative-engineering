# The Anisotropic Nature of FDM Parts

FDM parts are not isotropic, meaning they have different mechanical properties in different directions. This is a direct result of the layer-by-layer fabrication process, and it is the single most important factor to consider when designing parts for strength.

- **X-Y Plane (Horizontal)**: This is the strongest direction. The continuous polymer chains within each layer provide the maximum tensile strength of the material.
- **Z-Axis (Vertical)**: This is the weakest direction. The bond between layers is a thermal weld, which is significantly weaker than the continuous polymer chains within each layer. The Z-axis is the primary failure mode for FDM parts.

## Critical Orientation Factors

When orienting a part for printing, the following factors must be considered:

1. **Mechanical Strength**: The part should be oriented so that the layers are aligned perpendicular to the primary loads.
2. **Surface Quality**: The critical surfaces of the part should be positioned to achieve the best possible finish.
3. **Support Requirements**: The part should be oriented to minimize or eliminate the need for support structures.
4. **Print Time**: The Z-height of the part should be minimized to reduce print time.
5. **Dimensional Accuracy**: The orientation of the part can affect its dimensional accuracy due to shrinkage and warping.
