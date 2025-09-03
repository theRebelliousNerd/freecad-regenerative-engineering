# 1.5. Tolerances in FDM: A Practical Guide for Production-Grade Assemblies

Designers coming from a background in CNC machining or injection molding must adjust their expectations regarding dimensional tolerances. Industrial FDM systems, while precise, generally have wider tolerance bands than traditional subtractive or molding processes.

## Establishing Realistic Expectations

The typical dimensional tolerance for FDM is often cited as $\pm 0.5\%$ of the nominal dimension, with a lower limit of around $\pm 0.5$ mm. This means that for a 100 mm part, a deviation of up to 0.5 mm can be expected. These tolerances are influenced by a multitude of factors, including machine calibration, material properties, part geometry, and thermal effects. It is crucial to design assemblies with these realities in mind to avoid parts that do not fit together.

## Designing for Tolerance

Instead of pursuing impossibly tight tolerances, the DFAM approach is to design parts that accommodate the inherent variability of the process. This involves providing adequate clearance for mating parts. A set of practical rules of thumb can be applied during the design phase:

* **General Component Clearance:** Allow at least 0.5 mm of clearance around all internal components to account for printer tolerances and potential distortion.
* **Clearance Holes:** For holes intended for screws or pins to pass through freely (a slip fit), add 0.25 mm to the nominal diameter of the fastener. For more precise holes, it is often best to print them slightly undersized and drill them to the final dimension as a post-processing step.
* **Self-Tapping Holes:** For holes where a screw is intended to cut its own threads and bite into the plastic, subtract 0.25 mm from the nominal major diameter of the screw.

## Material Shrinkage

Material shrinkage is a distinct phenomenon from general printer tolerance. It is a predictable property of the material itself. Different polymers shrink at different rates as they cool. For example, PLA exhibits very low shrinkage (0.3-0.5%), making it excellent for dimensionally accurate parts. In contrast, ABS and Nylon can shrink significantly more (up to 2%), which must be compensated for in the CAD model. This is typically done by scaling the model up by the material's specific shrinkage percentage before slicing. Failing to account for this will result in parts that are consistently undersized.

| Material | Typical Dimensional Tolerance | Typical Shrinkage Rate | Design Compensation Notes |
| :--- | :--- | :--- | :--- |
| **PLA** | $\pm 0.5\%$ (lower limit $\pm 0.5$ mm) | 0.3% – 0.5% | Dimensionally stable, low warping. Good for precise fits. Brittle. |
| **PETG** | $\pm 0.5\%$ (lower limit $\pm 0.5$ mm) | ~0.5% | Good layer adhesion, low shrinkage. Can be stringy. Good for watertight applications. |
| **ABS** | $\pm 0.5\%$ (lower limit $\pm 0.5$ mm) | 0.8% – 1.5% | Prone to warping and cracking; requires a heated bed and enclosure. Can be acetone smoothed. |
| **ASA** | $\pm 0.5\%$ (lower limit $\pm 0.5$ mm) | ~0.8% | Similar to ABS but with superior UV resistance. Requires an enclosure. |
| **Nylon 12** | $\pm 0.3\%$ (lower limit $\pm 0.3$ mm) | 1.5% – 2.0% | Strong and durable but highly hygroscopic (absorbs moisture), requiring drying before printing. Prone to warping. |
