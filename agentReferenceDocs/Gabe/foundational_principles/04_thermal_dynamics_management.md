# 1.4. Managing Thermal Dynamics: Mitigating Warping and Shrinkage Through Design

All thermoplastic materials used in FDM shrink as they cool from their extrusion temperature. When this cooling occurs unevenly across a part, it induces internal stresses that can cause the part to deform and lift off the build plate, a phenomenon known as warping. Large, flat surfaces are particularly susceptible to this effect.

## Design-Based Solutions

While hardware solutions like heated beds and enclosures are essential, many thermal issues can be mitigated directly within the CAD model. The same principles that benefit first-layer adhesion also combat warping. Sharp corners, especially on the base of a model, act as concentration points for thermal stress, making them the primary locations where warping begins. By replacing these sharp corners with generous radii, the stress is distributed more evenly, significantly reducing the tendency for the corners to lift.

Avoiding large, solid, flat bases is another key strategy. As will be discussed in the section on automated part ejection, designing parts with minimal contact area on the build plate—such as using a shallow dome instead of a flat bottom—not only aids in removal but also drastically reduces the surface area susceptible to the differential cooling that causes warping.
