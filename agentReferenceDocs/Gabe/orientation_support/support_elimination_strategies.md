# Support Elimination Strategies

The goal of support-free design is to create parts that can be printed without the need for support structures. This is achieved by leveraging the natural capabilities of the FDM process and by incorporating intelligent design features into the part itself.

## The 45-Degree Rule

The most fundamental principle of support-free design is the 45-degree rule. This rule states that an FDM printer can reliably print overhangs up to a 45-degree angle from the vertical without the need for support.

| Overhang Angle | Support Required | Print Quality |
|---|---|---|
| 0-45° | No | Excellent |
| 45-60° | Maybe | Good (material dependent) |
| 60-75° | Usually | Fair |
| 75-90° | Always | Poor without support |

## Chamfer and Fillet Strategy

Chamfers and fillets are powerful tools for creating self-supporting geometries.

- **Chamfers**: A 45-degree chamfer can be used to transform a 90-degree overhang into a self-supporting 45-degree angle.
- **Fillets**: A fillet can be used to create a smooth transition between a vertical wall and a horizontal surface, which can help to prevent warping and improve surface finish.

## Advanced Support Elimination Techniques

- **Teardrop Holes**: Replace circular holes in horizontal orientations with teardrop shapes. The top of the teardrop is a self-supporting 45-degree angle.
- **Bridge Optimization**: Design for successful bridging by keeping unsupported spans under 10mm and optimizing the bridge settings in the slicer.
- **Diamond and Hexagonal Holes**: Use diamond or hexagonal holes instead of circular holes in vertical walls. These shapes can be printed without support.
- **Arc Overhangs**: A technique developed by Steven McCulloch that allows for the printing of extreme overhangs by extruding individual self-supporting arcs.
