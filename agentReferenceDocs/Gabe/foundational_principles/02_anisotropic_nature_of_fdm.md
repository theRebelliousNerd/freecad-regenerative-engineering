# 1.2. The Anisotropic Nature of FDM

Perhaps the most critical mechanical characteristic of FDM parts is their anisotropic nature—they exhibit different strength properties depending on the direction of the applied load. This is a direct consequence of the layer-by-layer construction.

## Designing for Layer Adhesion

The bond between adjacent extruded lines within a single layer (in the XY-plane) is very strong, as the molten plastic fuses together. However, the bond between successive layers (along the Z-axis) is weaker, representing a potential plane of failure. An FDM part is, in essence, a laminate of plastic sheets. Consequently, parts are significantly stronger when tensile or bending forces are applied parallel to the layers (in the XY-plane) and are weakest when these forces are applied perpendicular to the layers (along the Z-axis), which can pull the layers apart.

For production design, this means that part orientation is not just a matter of fitting a model on the build plate; it is a critical engineering decision. The designer must anticipate the primary load paths the part will experience in its application and orient the model in the slicer such that these forces are aligned with the XY-plane. For example, a simple hook designed to bear a hanging load should be printed lying on its side, not standing upright. Printing it upright would place the maximum tensile stress directly on the layer lines, leading to a high probability of failure.

## Stress Concentration

The anisotropic weakness of FDM parts is exacerbated by stress concentrations. Sharp internal corners in a design act as stress risers, concentrating forces at a single point and initiating cracks that can propagate along the layer lines, leading to delamination and catastrophic failure. The inclusion of fillets (rounded internal corners) is therefore not merely an aesthetic choice but a crucial structural requirement. Fillets distribute the stress over a larger area, mitigating the risk of layer separation and significantly increasing the part's load-bearing capacity.
