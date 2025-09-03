# Support Optimization When Unavoidable

While the goal of DFAM is to eliminate supports, there are some cases where they are unavoidable. In these cases, it is important to optimize the support structures to minimize material usage, print time, and post-processing labor.

## Support Type Selection

- **Tree Supports (Recommended 2024-2025)**:
  - **Advantages**: Use 50-70% less material than traditional supports, are easier to remove, and result in a better surface finish.
  - **Best for**: Organic shapes, scattered support needs, delicate features, and production parts.
- **Traditional Supports**:
  - **When to use**: For large flat overhangs, dense support requirements, and when maximum stability is needed.

## Support Settings Optimization

- **Support Density**: 10-20% for tree supports, 15-25% for traditional supports.
- **Z-Distance**: 0.2mm for easy removal.
- **X-Y Distance**: 0.8mm to prevent fusion.
- **Support Interface**: Enable for a better surface finish.
- **Interface Density**: 75-90%.
- **Pattern**: Gyroid or Lines.

## Support Removal Strategies

- **Design for Easy Removal**:
  - **Breakaway Tabs**: Design weak points into the support structure to make it easier to remove.
  - **Support Shields**: Use a support shield to protect the surface of the part from the support structure.
  - **Access Channels**: Design access channels to make it easier to get tools in to remove the supports.
  - **Minimal Contact**: Minimize the contact area between the support structure and the part.
  - **Material Selection**: Use a soluble support material, such as PVA, for parts with complex internal geometries.
