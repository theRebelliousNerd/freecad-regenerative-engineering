# Advanced Orientation Techniques

For complex geometries, it may be necessary to use more advanced orientation techniques to achieve the desired results.

## Multi-Part Strategy for Complex Geometries

- **When to Split Parts**:
  - When multiple optimal orientations are needed for different features of the part.
  - When it is impossible to eliminate supports for the part as a whole.
  - When the strength requirements of the part are in conflict.
  - When the assembly time is less than the support removal time.
- **Split Design Guidelines**:
  - Cut the part along natural seam lines.
  - Design self-aligning features, such as pins and holes.
  - Include channels for adhesive.
  - Maintain a consistent wall thickness at the joints.

## Production-Specific Orientation

- **Automated Ejection Optimization**:
  - Minimize the bed contact area to less than 10% of the part's footprint.
  - Use a 45-degree base angle to make the part easy to eject.
  - Use a single edge or corner as the contact point.
  - Use a smooth bottom surface with no bed adhesion features.
- **Batch Production Orientation**:
  - Maximize the number of parts per build plate.
  - Standardize the orientation across all variants of the part.
  - Enable consistent quality.
  - Minimize support universally.
  - Design for nesting efficiency.

## Material-Specific Orientation Strategies

- **PLA**: Low warping, so large flat bases are acceptable. Brittle, so avoid layer-aligned loads.
- **ABS**: High warping, so minimize bed contact. Use a brim or raft for adhesion.
- **PETG**: Moderate warping, so balance the contact area. Excellent layer adhesion, so more orientation freedom.
- **TPU**: Flexible layers, so orient for the bend direction. No bridging, so avoid unsupported spans.
