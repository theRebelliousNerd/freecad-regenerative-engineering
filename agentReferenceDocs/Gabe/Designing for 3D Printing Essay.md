

# **Design for Mass Production: A Technical Synthesis of Slant 3D's FDM Manufacturing Principles for Engineers**

## **Introduction: A Paradigm Shift from Prototyping to Production**

The maturation of Fused Deposition Modeling (FDM) has precipitated a critical shift in its application, moving from a tool primarily for rapid prototyping to a viable technology for mass production.1 This evolution demands a corresponding paradigm shift in design philosophy. Designing for a single prototype, where manual post-processing and iterative adjustments are acceptable, is fundamentally different from designing for a production run of ten thousand units on a large-scale print farm. For the seasoned engineer, accustomed to the principles of Design for Manufacturing (DFM) for established processes like injection molding or CNC machining, FDM presents a unique and often counter-intuitive set of constraints and opportunities.2 This report serves as a technical synthesis of the design principles for mass production FDM, as articulated through the extensive video library of Slant 3D, a company operating at the forefront of this industrial transformation.5

At the heart of the Slant 3D methodology is the concept of the "Digital Warehouse".7 This model reimagines the supply chain by storing products not as physical inventory on a shelf, but as digital files on a server, ready to be manufactured on-demand by a farm of thousands of FDM printers operating 24/7.7 This approach offers unparalleled flexibility, allowing for real-time design updates and eliminating the substantial capital investment and risk associated with traditional tooling and inventory management.7 It represents a more sustainable manufacturing pathway, drastically reducing the carbon footprint associated with global shipping and warehousing by localizing production.8 However, the successful implementation of the Digital Warehouse is entirely predicated on a specialized and rigorous approach to Design for Additive Manufacturing (DFAM). The parts must be designed from inception to be produced reliably, efficiently, and with minimal human intervention across a distributed, and inherently variable, manufacturing system.

This report is structured to provide the experienced engineer with a comprehensive framework for this new mode of thinking. It will deconstruct the core principles that govern FDM at scale, moving from foundational geometric rules to advanced strategies for structural integrity, precision tolerancing, and cost optimization. The analysis acknowledges the specific constraints of its source material—the publicly available video content of the Slant 3D YouTube channel. While this provides direct insight into the practical methods of a leading production house, it also means that full, verbatim transcripts for many instructional videos are not available, requiring a synthesis of visual and descriptive information.5

A critical examination of Slant 3D's educational content reveals a strategy that extends beyond simple instruction. By systematically teaching a specific DFAM methodology, the company is actively building a manufacturing ecosystem. This educational outreach serves to pre-qualify potential clients for its mass-production services, such as the Teleport platform, by creating a standardized design language optimized for its own print farm infrastructure.9 The design rules promulgated—such as minimizing bed contact to enable automated part ejection or using textures to obviate manual post-processing—are not merely general best practices; they are specific optimizations that directly reduce Slant 3D's internal operational costs, particularly labor.4 Consequently, the educational channel functions as a crucial component of the company's manufacturing apparatus, reducing friction in client onboarding, improving the manufacturability of submitted designs, and ultimately enhancing the efficiency and profitability of its production facilities. The engineer learning these principles is, in effect, learning to interface directly and efficiently with the factory of the future.

## **Part I: Foundational Principles of Design for Additive Manufacturing (DFAM)**

The successful application of FDM for mass production hinges on a set of foundational design rules that account for the physics of the layer-by-layer extrusion process. These principles, synthesized from Slant 3D's "8 Essential Design Rules for Mass Production 3D Printing," form a unified system for mitigating the common failure modes of FDM, ensuring that parts are not only functional but also manufacturable with high yield and minimal cost.15 This system represents a shift from designing for an idealized machine to designing for robustness within a real-world, high-variability production environment.

### **1.1 Rule 1: Minimum Feature and Wall Thickness**

The most fundamental constraint in FDM design is the physical dimension of the extruded filament. For a part to be structurally sound and reliably printable, its features must be designed with the nozzle diameter as the basic unit of measurement. The standard nozzle size in most production FDM printers is 0.4 mm. To create a solid, non-porous vertical wall, a minimum of two perimeters is required. This dictates a minimum reliable wall thickness of approximately 0.8 mm, which is often rounded up to a conservative 1 mm to account for slight variations in extrusion.15 Any feature designed to be thinner than this risks being unprintable or structurally compromised.

This principle extends to other positive features. For example, pins or posts are common points of failure, susceptible to shearing along layer lines. To ensure robustness, such features should have a minimum diameter of at least 3 mm.16 This provides sufficient cross-sectional area to resist operational stresses. This rule presents a direct contrast to DFM for injection molding, where engineers strive for the thinnest possible walls to reduce material cost, shorten cycle times, and prevent cosmetic defects like sink marks. In FDM, prioritizing wall thickness is essential for part integrity.

### **1.2 Rule 2: Overhang Management and Support Elimination**

One of the most significant drivers of cost and quality variation in FDM is the need for support material. Supports are temporary structures printed to hold up overhanging features that would otherwise be extruded into open air. However, they introduce substantial drawbacks: they increase material consumption and print time, require manual labor for removal, and leave a poor surface finish on the areas they touch.17 For mass production, where minimizing labor is paramount, designing for support-free printing is a primary objective.19

The common guideline is the "45-degree rule," which states that most printers can reliably print overhangs up to a 45-degree angle from the vertical without support. Slant 3D's methodology refines this into an active design strategy: instead of merely avoiding steep overhangs, the engineer should proactively transform them into self-supporting features. This is most commonly achieved by adding a 45-degree chamfer or a fillet underneath a horizontal feature.15 For instance, a rim on an electrical enclosure that protrudes at 90 degrees would require a full scaffold of support material; adding a chamfer beneath it allows the feature to build upon itself layer by layer, completely eliminating the need for supports and the associated costs.21 This proactive geometric modification is a cornerstone of efficient DFAM.

### **1.3 Rule 3 & 8: First Layer Optimization and Minimized Bed Contact**

In a print farm environment, two rules are inextricably linked to production automation: the reliability of the first layer and the ease of part removal. The first layer is the foundation of the entire print; if it fails to adhere properly to the print bed, the entire part will fail. To ensure high reliability across thousands of prints, the geometry of the first layer should be as simple as possible.15 This means avoiding sharp corners, which can peel up, and fine details like text, which may not resolve cleanly. The ideal first layer approaches a simple, continuous perimeter, like a circle or a rounded rectangle, to maximize adhesion and minimize failure points.

This principle connects directly to the goal of automated part ejection. A part with a large, flat base that covers a significant portion of the print bed will adhere very strongly, often requiring manual force and a scraper to remove.15 This is a bottleneck in a mass production workflow. The solution is to design the part to have minimal contact with the bed. This is frequently achieved by orienting the part at a 45-degree angle, allowing it to rest on a single edge or corner.4 This small contact point provides enough adhesion for a successful print but is weak enough that the part can be automatically knocked off the build plate by the printer's mechanics or a secondary system. This orientation strategy not only enables "lights-out" manufacturing but also improves part quality by minimizing the "elephant's foot" effect (where the first layer squishes outward) and ensuring a more uniform surface texture across the part.4

### **1.4 Rule 4: The Importance of Rounded Geometry (Fillets)**

The instinct in many CAD environments is to work with sharp, precise corners. For FDM production, however, this is inefficient. A 3D printer's motion system must decelerate to almost a complete stop to navigate a sharp 90-degree corner, then accelerate again in the new direction. This constant change in velocity adds significant time to a print.15

By rounding, or filleting, all vertical edges, the print head can maintain a much higher average speed, moving through the corner in a smooth, continuous arc, much like a race car taking a rounded turn.15 This seemingly minor design change can lead to a noticeable reduction in print time, which translates directly to lower cost at scale. Furthermore, rounded edges produce a part that is aesthetically more pleasing and mechanically more robust by reducing the stress concentrations that occur at sharp internal corners.

### **1.5 Rule 5: Volumetric Design (Avoiding Cavities)**

A common practice in traditional manufacturing is to hollow out or "shell" parts to save material. This is often a counterproductive strategy in FDM.15 FDM technology excels at creating complex internal structures at no additional cost. Instead of creating a large, unsupported internal cavity bounded by thin walls, it is far more effective to design the part as a solid volume and allow the slicing software to fill it with a low-density internal lattice, or "infill".23

This honeycomb-like internal structure provides support to the outer walls from all directions, making the part significantly stronger and stiffer than a hollow equivalent. A part with 20% gyroid infill, for example, behaves like a composite structure, distributing loads efficiently while using a fraction of the material of a solid part.24 This approach leverages a unique capability of additive manufacturing, turning what would be solid, heavy, and slow-to-print sections into lightweight, strong, and efficient structures. The engineering mindset must shift from "how can I remove material?" to "how can I best use volume?"

### **1.6 Rule 6: Surface Finish as a Design Choice (Textures)**

The visible layer lines on an FDM part are an inherent artifact of the manufacturing process. A common impulse is to try to eliminate them by reducing the layer height, which creates a higher-resolution print. However, this dramatically increases print time and, therefore, cost. A more elegant and economical solution is to treat the surface finish as a design feature.15

By applying a subtle (or pronounced) texture to the surfaces of a model directly in the CAD software, the layer lines can be effectively camouflaged.4 The texture breaks up the uniform, parallel lines, making them visually merge into the overall pattern. This transforms a potential cosmetic defect into a deliberate aesthetic choice. This technique is particularly effective when combined with non-traditional part orientations, as it allows the texture to be applied more uniformly across the part's surfaces.4 This approach avoids the high cost of high-resolution printing and the labor cost of manual post-processing (like sanding or vapor smoothing), making it a powerful tool for producing aesthetically pleasing parts at scale.

### **1.7 Rule 7: Designing for Process Variation with Compliance**

The final foundational rule serves as a gateway to the more advanced principles of tolerancing. It posits that instead of striving for absolute dimensional accuracy—a difficult and costly goal in a high-variability process like FDM—it is better to design parts that can accommodate variation.15 This is the principle of compliance.

For features that require a precise fit, such as a hole for a pin, the design should incorporate elements that allow it to flex or deform. This can be achieved through cutouts around the feature or by using specialized geometries like "grip fins".15 By building flexibility directly into the design, the part becomes robust to the inherent process variations, such as material shrinkage or minor machine miscalibrations. This philosophy of designing for process immunity, rather than chasing process perfection, is what enables reliable, high-yield production in a large print farm.

The following table provides a quick-reference consolidation of the most critical numerical parameters derived from these foundational rules.

| Parameter | Recommended Value | Rationale | Source(s) |
| :---- | :---- | :---- | :---- |
| Minimum Wall Thickness | 1.0 mm | Ensures a stable, non-porous wall using a standard 0.4 mm nozzle (2 perimeters). | 15 |
| Minimum Pin Diameter | 3.0 mm | Provides sufficient cross-sectional area to prevent shear failure along layer lines. | 16 |
| Interlocking Part Clearance | 0.5 mm | Accounts for FDM process variations, thermal expansion, and layer inconsistencies to ensure a functional fit. | 16 |
| Support-Free Overhang | 45∘ | Standard angle that most FDM printers can produce without support material, often extendable with chamfers. | 15 |

## **Part II: Engineering for Mechanical Performance and Structural Integrity**

Beyond basic manufacturability, parts designed for real-world applications must meet specific performance criteria for strength and durability. For FDM, achieving this requires a deep understanding of the material science of layered plastics and a set of design strategies that directly address the unique mechanical properties of the process. This involves a complete inversion of certain traditional manufacturing goals, such as part consolidation, in favor of techniques that optimize for the physics of filament deposition.

### **2.1 The Anisotropic Nature of FDM Parts**

The most critical principle governing the strength of an FDM part is anisotropy. An object produced via FDM is not a homogenous, isotropic solid. It is a laminate composite, built from layers of fused thermoplastic. The bond *within* a single extruded line (in the X-Y plane) is exceptionally strong, as it is essentially a solid piece of plastic. However, the bond *between* layers (in the Z-axis) is a thermal weld formed as a new hot layer is deposited onto a previously cooled one. This inter-layer bond is consistently the weakest point of the part.28

Consequently, an FDM part will exhibit significantly different mechanical properties depending on the direction of the applied load. It is strong against forces applied parallel to the build plate (in the X-Y plane) but is comparatively weak against tensile or shear forces applied perpendicular to the build plate, which act to pull the layers apart.4 All subsequent design decisions for structural components must be made with this fundamental constraint in mind.

### **2.2 Strategic Part Orientation for Load Bearing**

Given the anisotropic nature of FDM parts, print orientation becomes the single most important factor in determining the functional strength of a component. The design process for a load-bearing part must begin with a thorough analysis of the anticipated load paths. The part must then be oriented on the virtual build plate in the CAD or slicer software such that the primary tensile and bending stresses are aligned with the strong X-Y plane.18

Consider a simple L-shaped bracket designed to support a shelf. If printed standing up (in an "L" orientation), the corner of the bracket, which experiences the highest bending stress, would be subject to forces trying to delaminate the layers. The part would be very weak and likely fail. The correct approach is to print the bracket lying flat on its side. In this orientation, the layers run the length of both arms of the bracket. The bending forces are now acting against the continuous, solid extrusions of the X-Y plane, resulting in a dramatically stronger and more reliable part.28 This analysis must be the first step for any functional design.

### **2.3 Part Splitting: A Counter-Intuitive Strength Multiplier**

In many cases, a complex part will be subjected to loads from multiple directions, making it impossible to find a single print orientation that is optimal for all features. In traditional manufacturing, the goal is often part consolidation to reduce assembly steps and tooling costs. For FDM, the opposite strategy is frequently superior: splitting a single part into multiple pieces to maximize the strength of each piece.4

This technique involves decomposing a component into simpler geometric elements, printing each element in its own ideal orientation for strength, and then designing an effective joinery method for reassembly. An analysis of this method demonstrated that a simple bracket, when split into two pieces that were printed in their optimal orientations and then combined, was able to withstand nearly twice the load before failure compared to the same bracket printed as a single piece.4 The minor increase in complexity from adding an assembly step is a small price to pay for a 100% increase in mechanical performance. This requires the engineer to unlearn the instinct for part consolidation and instead view components as assemblies of optimally oriented features. Techniques like printed dovetails or snap-fits can be used to create strong, simple connections between the split components.30

### **2.4 Structural Reinforcement: Ribs, Gussets, and Infill**

Once a part is correctly oriented, its stiffness and strength can be further enhanced through structural reinforcement. While infill provides a good baseline of internal support, for targeted load-bearing applications, the use of designed-in ribs and gussets is more efficient.21 These features function identically to their counterparts in injection molding or civil engineering, adding structural integrity with minimal material addition.

The key principle for effective rib placement is to add height and material in the direction of the applied load to increase the area moment of inertia and resist bending.31 For a flat plate supported at both ends and loaded in the middle, ribs should be added perpendicular to the plate, running parallel to the span. This can reduce deflection by an order of magnitude with only a small increase in material and print time.31 Best practices suggest that rib thickness should be approximately 60-80% of the main wall thickness to ensure proper printing and avoid cosmetic defects. Gussets should be used to reinforce features like bosses or walls that are perpendicular to a base, preventing them from being bent or broken off under load. The strategic use of these features allows for the creation of strong, lightweight, and cost-effective parts, far superior to simply increasing infill percentage across the entire model.24

## **Part III: A Systematic Approach to Tolerancing and Precision Assemblies**

Achieving a reliable and repeatable fit between mating parts is one of the most significant challenges in FDM 3D printing, especially in a mass production environment. The inherent variability of the process makes traditional tolerancing methods, which rely on achieving precise nominal dimensions, largely ineffective. The Slant 3D methodology addresses this challenge not by attempting to control the process with impossible precision, but by designing parts that are functionally immune to that process's inherent variation. This approach, which mirrors the principles of robust design, is the key to creating successful assemblies at scale.

### **3.1 The Fallacy of Chasing Nominal Dimensions**

Engineers new to FDM often fall into a frustrating cycle of trial and error: a part is designed to its exact nominal dimensions, printed, and found not to fit. The engineer then adjusts the CAD model by a small offset or tweaks a slicer setting like "horizontal expansion compensation" and prints again.7 This approach is untenable for production. It fails because it attempts to correct for a complex system of variables with a single, static offset.

The dimensional accuracy of an FDM part is affected by numerous "noise" factors that are difficult to control across a large farm of printers.13 These include:

* **Material Shrinkage:** All thermoplastics shrink as they cool from their extrusion temperature. The rate of shrinkage varies significantly between materials like PLA, PETG, and ABS, and can even be affected by the speed at which the part cools.29  
* **Filament Variation:** The diameter of a filament can vary slightly along its length, and pigments used for color can alter its thermal and flow properties, leading to dimensional differences between prints of different colors from the same material type.13  
* **Machine Quirks:** Every printer in a farm has its own minor variations in calibration, belt tension, and component wear, leading to subtle but meaningful differences in output.13

Attempting to chase a perfect nominal dimension in the face of these variables is a losing battle. The robust design approach, instead, accepts this variation as a given and focuses on creating a design whose function (a perfect fit) is unaffected by it.

### **3.2 Foundational Techniques for Fitment**

Before employing more advanced strategies, several basic geometric principles can significantly improve the ease of assembly and the reliability of fits. These techniques work by guiding parts together and minimizing the negative effects of friction and surface imperfections.

* **Rounded Edges and Chamfers:** Just as rounding vertical edges improves print speed, adding chamfers or rounds to the leading edges of mating parts (like a pin and a hole, or a lid and a box) acts as a guide during assembly.7 This prevents jamming and makes the initial alignment of the parts far less sensitive to the user's precision.  
* **Reduced Contact Surfaces:** The friction between two flat, 3D printed surfaces can be substantial, especially over a large area. By designing mating parts to make contact only on smaller, dedicated surfaces, the overall friction is reduced.7 This makes the parts easier to assemble and disassemble and minimizes the impact of any surface warping or imperfections.

### **3.3 The Power of Compliant Mechanisms**

The primary tool for achieving tolerance immunity is the compliant mechanism. A compliant mechanism is a flexible structure that transfers force or motion through elastic deformation, rather than through rigid-body joints.34 In essence, it is a spring that is integrated directly into the body of the part. Because FDM can create complex geometries in a single piece, it is an ideal manufacturing method for these advanced structures.14

In the context of tolerancing, compliant features are used to build a "range of acceptance" into a design. Instead of a lid needing to be exactly 100.0 mm wide to fit a 100.0 mm box, a compliant lid is designed to flex. It might have thin, curved sections that act as leaf springs.7 This allows the lid to easily fit a box that is 99.8 mm wide (by expanding slightly) or one that is 100.2 mm wide (by compressing slightly), providing a secure, snug fit in either case.7 The design itself absorbs the dimensional variation of the manufacturing process.

A prime example of this principle in a complex application is the 3D printed Nerf blaster designed by Mark Rober in collaboration with BYU's Compliant Mechanisms Research Group.6 The entire firing mechanism, which would traditionally be a complex assembly of multiple rigid parts, pins, and springs, is printed as a single, monolithic piece. The function is achieved entirely through the controlled flexing of its geometric features.35 This demonstrates the power of compliance not just for simple fits, but for creating sophisticated, functional mechanical systems.

### **3.4 Specialized Fitment Features: Design and Application**

Building on the general principle of compliance, several specific, named features have been developed to solve common fitment problems in FDM.

* **Grip Fins:** For applications requiring a hole that can securely grip a rod or pin, especially one that may be removed and reinserted multiple times, "grip fins" are an ideal solution.15 These are a series of small, flexible cantilevers or lamellas designed into the circumference of a hole.33 The inner diameter of the fins is designed to be slightly smaller than the diameter of the pin. When the pin is inserted, the fins flex outward, acting as integrated springs that exert a constant, gentle gripping force.39 This provides a secure friction fit that is highly repeatable and tolerant of variations in both the hole and pin diameters.13  
* **Living Hinges:** A living hinge is a thin, flexible web of material that connects two rigid sections, allowing them to bend relative to one another. FDM is capable of producing extremely durable living hinges that can withstand thousands of flexion cycles, enabling the creation of complex objects that are printed flat and then folded into their final 3D shape.40 This technique eliminates the need for separate hinge components and assembly, reducing part count and cost.4  
* **Snap-Fits and Pins:** Designing robust snap-fits for FDM requires careful attention to the anisotropic nature of the material. The flexible cantilever arm of the snap-fit must be oriented on the build plate so that the bending stress is applied along the strong X-Y plane, not against the weak Z-axis layer bonds.30 Pins, another common failure point, can be made virtually unbreakable by avoiding long, thin designs and instead using features like a teardrop or diamond cross-section for holes printed horizontally, which provides a self-supporting top surface and a more accurate circular shape.10

### **3.5 Design for Assembly (DFA)**

For multi-component products, the principles of Design for Assembly are critical. The goal is to create parts that fit together easily and reliably. For FDM, this starts with a standard clearance. A general rule of thumb for a loose or free fit between two parts is to design a gap of 0.4 mm to 0.5 mm.16 This provides enough space to account for the cumulative process variations and prevent parts from fusing together. For a tighter press fit, this clearance can be reduced to 0.2 mm or less, depending on the material and application.44

Beyond simple clearances, FDM allows for the use of advanced geometric joinery that can reduce or eliminate the need for fasteners. Dovetail joints, for example, are trivial to print and provide a strong, self-aligning connection that constrains motion in multiple axes.30 Sideways "V-groove" connectors and other interlocking features can be designed to create robust assemblies that are simple to put together, leveraging the geometric freedom of 3D printing to simplify the final manufacturing steps.30

## **Part IV: Optimizing Design for Cost and Production Velocity**

In any mass production context, cost is a primary driver of design decisions. For FDM, the economics are uniquely transparent and directly influenced by the geometry of the part. Unlike injection molding, where the dominant cost is the upfront investment in tooling, the cost of an FDM part is almost entirely a function of the machine time required to print it and the labor needed to handle it.47 This gives the design engineer unprecedented control over the final per-part cost. By making intelligent choices in the CAD stage, production time can be minimized, and labor can be eliminated, leading to dramatic cost reductions.

### **4.1 The Print Time-Cost Equation**

The single largest variable in the cost of an FDM part is print time.48 This time is determined by two main factors: the total volume of material that needs to be extruded and, more importantly, the total number of layers, which is dictated by the part's height in the Z-axis. Every new layer requires the printer to perform a full set of movements to trace the part's cross-section, making Z-height a critical factor in overall print duration.49 Therefore, any design strategy that reduces either the material volume or the Z-height will directly and proportionally reduce the manufacturing cost.23

### **4.2 Geometric Strategies for Cost Reduction**

Several geometric and orientation strategies can be employed to manipulate the print time-cost equation favorably.

* **Diagonal Orientation:** One of the most powerful and non-obvious techniques for reducing cost is to orient parts diagonally on the build plate.22 For any rectangular part, its diagonal dimension is shorter than the sum of its length and width. By rotating the part 45 degrees, it is possible to fit a larger object within a given build volume. More importantly, for long, thin parts, printing them diagonally can significantly reduce their effective Z-height compared to printing them flat, leading to a "wildly" reduced print time and cost.19 This simple rotation in the slicer is a "free" optimization that can have a massive impact on production efficiency.  
* **Designing for Nesting:** When producing many small parts, the efficiency of a print farm is maximized by packing as many components as possible onto a single build plate for each print run. This is known as nesting or batching.52 While modern slicer software can automate this process to some degree, designing parts with geometries that interlock or nest tightly can further improve plate density.53 This reduces the number of print jobs required for a given quantity, minimizing the non-printing overhead time (like heating and cooling) and maximizing machine throughput.  
* **Lattice Structures:** As discussed in the context of structural design, replacing solid volumes with internal lattice structures is a key strategy for reducing material usage and print time.55 Advanced topology optimization software can be used to generate highly efficient lattices that maintain strength only where it is needed, cutting part mass by 25% to 70% or more.55 This directly translates to faster prints and lower material costs, making it an essential technique for optimizing functional parts.46

### **4.3 Eliminating Post-Processing Costs**

A significant hidden cost in many manufacturing processes is manual labor for post-processing. In FDM, the two most common labor-intensive steps are support removal and surface finishing. The design principles outlined in previous sections are the primary tools for eliminating these costs.

By designing parts with self-supporting angles and chamfers, the need for support material is removed, and with it, the labor required to break away and clean up those supports.17 Similarly, by using designed-in textures to hide layer lines, the need for manual sanding, filling, or vapor smoothing is obviated.4 Each of these design choices directly removes a human touchpoint from the production line, which is critical for achieving low costs at scale. The ideal part, from a production standpoint, is one that can be automatically ejected from the printer and go directly into a shipping box with zero manual intervention.15

## **Part V: Material Properties and Their Design Implications**

Material selection is a critical stage in the engineering design process, dictating a part's mechanical performance, environmental resistance, and cost. For FDM, the properties of the final printed part are a product of both the base polymer and the manufacturing process itself. The layer-by-layer fusion creates an anisotropic structure whose performance can differ significantly from that of an equivalent injection-molded part. Understanding the practical, as-printed properties of common thermoplastics is therefore essential for making informed design choices.

### **5.1 Comparative Analysis of Common Thermoplastics**

Data from systematic compression tests on FDM-printed samples provides valuable, real-world insights into material performance that go beyond generic datasheet values.56

* **PLA (Polylactic Acid):** Often perceived as a brittle, hobbyist-grade material, PLA exhibits surprisingly high compressive strength and stiffness in its printed form. In tests, it withstood the highest compressive load before failure, making it an excellent choice for parts subjected to static, high-pressure loads.56 Its primary drawback is a brittle failure mode, meaning it fractures suddenly rather than deforming, and it has a low glass transition temperature, making it unsuitable for high-heat environments.57  
* **PETG (Polyethylene Terephthalate Glycol) & ABS (Acrylonitrile Butadiene Styrene):** These materials occupy a middle ground, offering a good balance of strength, ductility, and thermal resistance, making them suitable for a wide range of functional parts.12 They are less stiff than PLA but more durable, failing in a more ductile manner. PETG is noted for having slightly better sound and vibration damping properties compared to PLA and ABS.58 ABS has a higher tendency to warp during printing due to greater thermal contraction, which must be accounted for in the design (e.g., by avoiding large, flat surfaces).27  
* **Nylon (Polyamide):** While known for its exceptional toughness, wear resistance, and high tensile strength in bulk form, printed Nylon performs poorly under pure compression. Its inherent flexibility causes it to buckle and deform at relatively low compressive loads.56 It is best suited for applications that leverage its toughness and low friction, such as gears or living hinges, rather than static structural supports.  
* **TPU (Thermoplastic Polyurethane):** As a flexible elastomer, TPU is in a class of its own. It is not designed for stiffness but for durability and elasticity. Under compression, it deforms significantly without fracturing, absorbing a large amount of energy.12 This makes it ideal for applications like seals, gaskets, vibration dampers, and compliant mechanisms that require repeated, large deformations.

The following table summarizes the quantitative results from compression testing of FDM-printed samples, providing a direct comparison for engineering selection.

| Material | Max Compressive Load (lbf) | Max Compressive Load (N) | Observed Failure Mode |
| :---- | :---- | :---- | :---- |
| PLA | \~530 | \~2362 | High Stiffness, Brittle Fracture |
| PETG | 485 | 2160 | Mid-Range Stiffness, Ductile Failure |
| ABS | 472 | 2100 | Mid-Range Stiffness, Ductile Failure |
| PA6 Nylon | 189 | 844 | Low Stiffness, Deformation/Buckling |

### **5.2 Designing for Specific Material Behaviors**

The choice of material has direct implications for the design geometry and application of the part.

* **Designing with PLA:** To leverage PLA's high stiffness, it should be used for rigid structural components that are primarily under compression. The design should actively avoid situations involving impact or shock loading due to its brittleness. Its low shrinkage makes it easier to hold tighter tolerances for non-compliant features compared to other materials.  
* **Designing with PETG/ABS:** The higher ductility of these materials makes them more forgiving for parts that may experience some bending or impact, such as snap-fit enclosures. Their greater thermal expansion means that designs relying on them for fitment should make more extensive use of compliant mechanisms to accommodate the increased potential for dimensional variation.27  
* **Designing with TPU:** When designing with TPU, the goal is to leverage its elasticity. Compliant mechanisms and living hinges made from TPU can undergo much larger deformations and more cycles than their rigid counterparts. Wall thicknesses and feature sizes must be carefully considered to achieve the desired level of flexibility versus stiffness.

## **Part VI: Applied DFAM: Case Studies and Analysis**

The true test of any design philosophy lies in its application to real-world products. By analyzing specific case studies featured by Slant 3D, it is possible to see how the foundational principles of DFAM are synthesized to create functional, cost-effective, and scalable products. These examples provide concrete illustrations of the abstract rules, bridging the gap between theory and practice.

### **6.1 Case Study: The "Stress Nut" Fidget Toy**

The "Stress Nut" is a fidget toy that successfully made the leap from a 3D printed product to the shelves of major retailers like Walmart, serving as a powerful testament to the viability of FDM for consumer goods.60 An analysis of its design reveals a masterclass in optimization for mass production FDM.

The product consists of only two parts: a large, threaded bolt and a matching nut.61 This simplicity is its greatest manufacturing strength. The threads are designed to be large and robust, with generous clearances, making them highly tolerant to the variations inherent in the FDM process. This ensures a smooth, satisfying action without the need for high-precision printing. The overall form of both components is simple, with no complex overhangs or delicate features, allowing for very fast print times and eliminating the need for support material entirely. The design requires minimal assembly—the two parts simply thread together. This combination of tolerance-forgiving geometry, high-speed printability, and zero post-processing makes the Stress Nut an ideal product for automated, large-scale production on a print farm.60 The case study demonstrates that a well-designed product can leverage FDM to bypass the high initial cost of injection molding, allowing for market entry and scaling with minimal capital risk.

### **6.2 Case Study: Electrical Enclosures**

Electrical enclosures are a common industrial application for FDM, where the technology's ability to produce custom, low-to-mid-volume runs is a significant advantage over traditional machining.21 The design principles for these parts directly address key cost and quality drivers.

Structurally, enclosures must be rigid. This is achieved efficiently not by using thick, solid walls, but by employing thin walls reinforced with a grid of internal ribs.21 This approach provides maximum stiffness with minimum material and print time, a more controlled and engineered solution than simply relying on a percentage of generic infill. A common feature on enclosures is a protruding rim or lip for the lid, which often creates a 90-degree overhang. As previously discussed, this is a costly feature to print. The optimized design for an FDM enclosure replaces this sharp overhang with a 45-degree chamfer, making the feature self-supporting and eliminating costs.21 Most critically, for mass production, the enclosure is not printed flat on its largest face. Instead, it is oriented at a 45-degree angle to rest on an edge.15 This minimizes bed contact for automated ejection, ensures a uniform and aesthetically pleasing texture across all visible faces, and aligns the layers for optimal strength in the walls.

### **6.3 Case Study: Advanced Mechanisms (Compliant Blaster, Hinges)**

These case studies demonstrate how the foundational principles can be combined to create highly complex, functional parts that would be difficult or impossible to produce with other methods. The compliant Nerf blaster, for instance, integrates springs, triggers, and linkages into a single printed part.14 This is the ultimate expression of part consolidation enabled by FDM. It relies on a deep understanding of how thin features bend (leveraging material elasticity) and how to orient those features so that the bending occurs along the strong X-Y axis.

Similarly, various print-in-place hinges showcase the ability to create entire assemblies in a single print job.40 These designs require precise control over clearances to ensure that the moving parts of the hinge do not fuse together during printing, while also orienting the hinge pin for maximum shear strength. These advanced applications illustrate the end goal of this DFAM philosophy: to embed mechanical function directly into the geometry of the material, creating sophisticated products with minimal part count and zero assembly labor.

## **Conclusion: The Future of Manufacturing is Designed, Not Assembled**

The principles and strategies synthesized from the Slant 3D educational platform articulate a clear and compelling vision for the future of manufacturing. This vision is defined by a fundamental migration of complexity away from the physical factory floor and into the digital realm of the CAD file. In traditional manufacturing, achieving precision and function often relies on highly tuned machines, complex multi-part assemblies, and significant manual labor for finishing and integration. In the mass production FDM paradigm, these challenges are preemptively solved at the design stage.

The engineer, armed with an understanding of FDM's anisotropic nature and inherent variability, is empowered to create parts that are intrinsically robust, cost-effective, and scalable. Compliance is designed-in to accommodate process noise, eliminating the need for impossible tolerances. Supports are designed-out through intelligent geometric manipulation, removing the cost of manual labor. Strength is maximized by treating a part not as a monolith but as an assembly of optimally oriented features. Cost is controlled directly by manipulating Z-height and volume through part orientation and internal lattices. Functionality, from simple hinges to complex mechanisms, is embedded directly into the part's monolithic structure.

This approach elevates the role of the design engineer, making them the central architect of manufacturing efficiency. The mastery of this new language of DFAM is what unlocks the full potential of the "Digital Warehouse" concept: a truly agile, on-demand, and decentralized manufacturing ecosystem.9 As this technology continues to mature, the ability to design products that are born manufacturable will be the defining skill for the next generation of industrial innovation. The factory of the future will not be defined by its machines, but by the intelligence of the designs they produce.

#### **Works cited**

1. The rise of 3D printer farms | VoxelMatters \- The heart of additive manufacturing, accessed September 1, 2025, [https://www.voxelmatters.com/the-rise-of-3d-printer-farms/](https://www.voxelmatters.com/the-rise-of-3d-printer-farms/)  
2. Design like a pro with shadow lines \- 3D design for 3D printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=8dhFhU7Nl\_0](https://www.youtube.com/watch?v=8dhFhU7Nl_0)  
3. 360 LIVE: Tips & Tricks \- Designing for 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=x2N2D3\_0L4M](https://www.youtube.com/watch?v=x2N2D3_0L4M)  
4. Dfm | Hackaday, accessed September 1, 2025, [https://hackaday.com/tag/dfm/](https://hackaday.com/tag/dfm/)  
5. Slant 3D \- YouTube, accessed September 1, 2025, [https://www.youtube.com/channel/UC6QNjBn6KMq5-pe3OE11zZg/shorts](https://www.youtube.com/channel/UC6QNjBn6KMq5-pe3OE11zZg/shorts)  
6. Slant 3D \- YouTube, accessed September 1, 2025, [https://www.youtube.com/@slant3d](https://www.youtube.com/@slant3d)  
7. Design Compliant Lids for Perfect Tolerance Every Time | Design for 3D Printing: Lids: Vol. 2, accessed September 1, 2025, [https://www.youtube.com/watch?v=IZKh6lo9SP4](https://www.youtube.com/watch?v=IZKh6lo9SP4)  
8. Design for Mass Production 3D Printing: Spool Holder Exploration \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=YMk7EfbemGY](https://www.youtube.com/watch?v=YMk7EfbemGY)  
9. What We Do at Slant 3D \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=jj4qkWtrVIc](https://www.youtube.com/watch?v=jj4qkWtrVIc)  
10. Design Unbreakable Pins with Perfect Tolerances \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=uMA-Wt-z\_BU](https://www.youtube.com/watch?v=uMA-Wt-z_BU)  
11. How-to Design for Mass Production 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/playlist?list=PLkUv8\_afCbJ9zfaZxqL4AHBrGHqTaU9lo](https://www.youtube.com/playlist?list=PLkUv8_afCbJ9zfaZxqL4AHBrGHqTaU9lo)  
12. How Strong Are Common 3D Printing Materials? \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=5CFVcPYFEiE](https://www.youtube.com/watch?v=5CFVcPYFEiE)  
13. How to Design a Print with Perfect Tolerance EVERY Time \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=XKrDUnZCmQQ](https://www.youtube.com/watch?v=XKrDUnZCmQQ)  
14. The Secret Inside Mark Rober's 3D Printed Nerf Blaster | Design of Compliant Mechanisms, accessed September 1, 2025, [https://www.youtube.com/watch?v=O33g62Kwq9s](https://www.youtube.com/watch?v=O33g62Kwq9s)  
15. Design Rules for Mass Production 3D Printing \- Slant 3D, accessed September 1, 2025, [https://www.slant3d.com/slant3d-blog/8-essential-design-rules-for-mass-production-3d-printing](https://www.slant3d.com/slant3d-blog/8-essential-design-rules-for-mass-production-3d-printing)  
16. 3D Printing Design Rules \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=2PJa5gyDKOk](https://www.youtube.com/watch?v=2PJa5gyDKOk)  
17. 3D Printing Basics: Understanding and Managing Support Material \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=WYQbxIVLz6Y\&pp=0gcJCRsBo7VqN5tD](https://www.youtube.com/watch?v=WYQbxIVLz6Y&pp=0gcJCRsBo7VqN5tD)  
18. Design for 3D-Printing \- Rahix' Blog, accessed September 1, 2025, [https://blog.rahix.de/design-for-3d-printing/](https://blog.rahix.de/design-for-3d-printing/)  
19. Basic Design Tips to Lower Your Manufacturing Costs | High-Volume 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=-gm6hzbAqLk](https://www.youtube.com/watch?v=-gm6hzbAqLk)  
20. Scaling your CNC Projects for Success\! (master dfm principles) \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=Qr6VZT87eeE](https://www.youtube.com/watch?v=Qr6VZT87eeE)  
21. 3D Printing Electrical Enclosures \- Slant 3D, accessed September 1, 2025, [https://www.slant3d.com/slant3d-blog/3d-printing-electrical-enclosures](https://www.slant3d.com/slant3d-blog/3d-printing-electrical-enclosures)  
22. The Power of Diagonals: Design for Mass Production 3D Printing 1 \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=8TIhkxQNINY](https://www.youtube.com/watch?v=8TIhkxQNINY)  
23. Cavities Don't Help: Design for Mass Production 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=AURCtaRrUGM](https://www.youtube.com/watch?v=AURCtaRrUGM)  
24. How Infill Percentage Affects Strength, Speed, and Filament Use \- SOVOL, accessed September 1, 2025, [https://www.sovol3d.com/blogs/news/infill-percentage-3d-printing-strength-filament](https://www.sovol3d.com/blogs/news/infill-percentage-3d-printing-strength-filament)  
25. The Easiest Way to Instantly 10x Your Print Quality \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=scv4am8kbqs](https://www.youtube.com/watch?v=scv4am8kbqs)  
26. Avoid sharp edges : r/FixMyPrint \- Reddit, accessed September 1, 2025, [https://www.reddit.com/r/FixMyPrint/comments/14ojb65/avoid\_sharp\_edges/](https://www.reddit.com/r/FixMyPrint/comments/14ojb65/avoid_sharp_edges/)  
27. FDM 3D Printing Design Tips: Best Practices and Techniques for Stronger Prints, accessed September 1, 2025, [https://xometry.au/fdm-3d-printing-design-tips-best-practices-and-techniques-for-stronger-prints/](https://xometry.au/fdm-3d-printing-design-tips-best-practices-and-techniques-for-stronger-prints/)  
28. Designing STRONG parts: tips and tricks \- 3D design for 3D printing ..., accessed September 1, 2025, [https://www.youtube.com/watch?v=yP7\_qZ\_Mi78](https://www.youtube.com/watch?v=yP7_qZ_Mi78)  
29. How to design for FFF 3D printing, accessed September 1, 2025, [https://louisville.edu/amist/amist-print-farm/ultimaker-guide-on-how-to-design-for-fff-3d-printing](https://louisville.edu/amist/amist-print-farm/ultimaker-guide-on-how-to-design-for-fff-3d-printing)  
30. 3D Printed Joinery: Simplifying Assembly \- Markforged, accessed September 1, 2025, [https://markforged.com/resources/blog/joinery-onyx](https://markforged.com/resources/blog/joinery-onyx)  
31. Best Practices for Adding Ribs and Gussets to 3D Printed Parts for Structural Integrity, accessed September 1, 2025, [https://www.core77.com/posts/66446/Best-Practices-for-Adding-Ribs-and-Gussets-to-3D-Printed-Parts-for-Structural-Integrity](https://www.core77.com/posts/66446/Best-Practices-for-Adding-Ribs-and-Gussets-to-3D-Printed-Parts-for-Structural-Integrity)  
32. Parts that fit odd shaped objects \- 3D design for 3D printing pt4 \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=noYuQlQN8pw](https://www.youtube.com/watch?v=noYuQlQN8pw)  
33. How To Design 3D-Printed Parts With Tolerance In Mind | Hackaday, accessed September 1, 2025, [https://hackaday.com/2025/08/04/how-to-design-3d-printed-parts-with-tolerance-in-mind/](https://hackaday.com/2025/08/04/how-to-design-3d-printed-parts-with-tolerance-in-mind/)  
34. Rotating click spring : r/3Dprinting \- Reddit, accessed September 1, 2025, [https://www.reddit.com/r/3Dprinting/comments/1lukhge/rotating\_click\_spring/](https://www.reddit.com/r/3Dprinting/comments/1lukhge/rotating_click_spring/)  
35. How to create effective compliant mechanisms with 3D printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=xV36ITRjP\_4](https://www.youtube.com/watch?v=xV36ITRjP_4)  
36. Compliant Mechanisms that Roll Like GEARS\!?\! \-- \#VeritasiumContest \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=uvPSsUkLypY](https://www.youtube.com/watch?v=uvPSsUkLypY)  
37. Precise design: Correctly implementing tolerances in FDM 3D printing, accessed September 1, 2025, [https://www.3printr.com/precise-design-correctly-implementing-tolerances-in-fdm-3d-printing-2482913/](https://www.3printr.com/precise-design-correctly-implementing-tolerances-in-fdm-3d-printing-2482913/)  
38. Design for 3D Printing: Grip Fins \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=yzg\_NXM-NRs](https://www.youtube.com/watch?v=yzg_NXM-NRs)  
39. Design Better Holes | Improve Tolerances | Reduce Sagging | Design for Mass Production 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=Bd7Yyn61XWQ](https://www.youtube.com/watch?v=Bd7Yyn61XWQ)  
40. 5 Living Hinges for Mass Production 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=TiEyFle6lTM](https://www.youtube.com/watch?v=TiEyFle6lTM)  
41. Learn 15 Print-in-Place Mechanisms in 15 Minutes \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=AAKsl8zW-Ds](https://www.youtube.com/watch?v=AAKsl8zW-Ds)  
42. Slant 3D \- YouTube, accessed September 1, 2025, [https://www.youtube.com/channel/UC6QNjBn6KMq5-pe3OE11zZg/posts](https://www.youtube.com/channel/UC6QNjBn6KMq5-pe3OE11zZg/posts)  
43. Pins & Holes That Fit Every Time | Design for 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=Iyxp\_Rjz3wo](https://www.youtube.com/watch?v=Iyxp_Rjz3wo)  
44. 3D print material test tolerances (HOLE FITS) 2020 05 14 \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=Sf7wqIgOFq0](https://www.youtube.com/watch?v=Sf7wqIgOFq0)  
45. 3D Printed Connections and Mechanisms \- Course Snapshot \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=3vMCP9vJ95Q](https://www.youtube.com/watch?v=3vMCP9vJ95Q)  
46. How to Design Multi-Component Assemblies for 3D Printing: From CAD to Assembly \- Wefab AI: AI-Driven Contract Manufacturing for Hardware Innovators, accessed September 1, 2025, [https://wefab.ai/blog/how-to-design-multi-component-assemblies-for-3d-printing-from-cad-to-assembly/](https://wefab.ai/blog/how-to-design-multi-component-assemblies-for-3d-printing-from-cad-to-assembly/)  
47. How to reduce Teleport print costs? : r/3DprintEntrepreneurs \- Reddit, accessed September 1, 2025, [https://www.reddit.com/r/3DprintEntrepreneurs/comments/1l1tzrk/how\_to\_reduce\_teleport\_print\_costs/](https://www.reddit.com/r/3DprintEntrepreneurs/comments/1l1tzrk/how_to_reduce_teleport_print_costs/)  
48. Stop Wasting Time & Filament – This Infill Setting Will Change Everything\! \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=0X5DfUPoThk](https://www.youtube.com/watch?v=0X5DfUPoThk)  
49. How I Save Hours Off Every Single 3D Print\! \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=D-TKGT2BH9M](https://www.youtube.com/watch?v=D-TKGT2BH9M)  
50. Half your 3d printing time \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=BmgS1UvcjrU](https://www.youtube.com/watch?v=BmgS1UvcjrU)  
51. Stop 3d printing so slow\!\!\! (how to print faster) \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=MWhyCarNPbs](https://www.youtube.com/watch?v=MWhyCarNPbs)  
52. STOP Filling Your Build Plate | Design for 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=ZpmiK0aY9VM](https://www.youtube.com/watch?v=ZpmiK0aY9VM)  
53. We Designed the Perfect Snack Tray for Oreos & Milk | Design for 3D Printing \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=O7uwXBGHN3g](https://www.youtube.com/watch?v=O7uwXBGHN3g)  
54. Secrets to Better Surface Finish for 3D Printed Electrical Enclosures \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=W5WdUF4Y\_FI](https://www.youtube.com/watch?v=W5WdUF4Y_FI)  
55. 3D Printing Lattice Structures \- 3ERP, accessed September 1, 2025, [https://www.3erp.com/blog/3d-printing-lattice-structures/](https://www.3erp.com/blog/3d-printing-lattice-structures/)  
56. Belastungstest: Welches 3D-Druck-Material ist am stabilsten?, accessed September 1, 2025, [https://3druck.com/3d-druckmaterialien/belastungstest-welches-3d-druck-material-ist-am-stabilsten-52126573/](https://3druck.com/3d-druckmaterialien/belastungstest-welches-3d-druck-material-ist-am-stabilsten-52126573/)  
57. Advanced modeling for large-scale 3D printing: techniques from design to execution, accessed September 1, 2025, [https://www.sovol3d.com/blogs/news/advanced-modeling-for-large-scale-3d-printing-design-execution](https://www.sovol3d.com/blogs/news/advanced-modeling-for-large-scale-3d-printing-design-execution)  
58. Test Cone Platform \- PLA vs PETG vs ABS \- Cones & Z Axis Stiffness \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=iuSP3Qe7b3o](https://www.youtube.com/watch?v=iuSP3Qe7b3o)  
59. How Strong is ABS? \#3dprinting \#3dprinttest \#shortsvideo \- YouTube, accessed September 1, 2025, [https://m.youtube.com/shorts/d4OqOfiRIgU](https://m.youtube.com/shorts/d4OqOfiRIgU)  
60. How 3D Printing Got Stress Nut into Walmart | Real 3D Printed Products \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=G0QAsBj7j5k](https://www.youtube.com/watch?v=G0QAsBj7j5k)  
61. Fidget Toy, Fidget Nut, Fun Gift, 3D Printed Decompression Desk Toy \- Etsy, accessed September 1, 2025, [https://www.etsy.com/listing/1580365115/fidget-toy-fidget-nut-fun-gift-3d](https://www.etsy.com/listing/1580365115/fidget-toy-fidget-nut-fun-gift-3d)  
62. Redesigning a Tape Dispenser for 3D Printing \#designfor3dprinting \- YouTube, accessed September 1, 2025, [https://www.youtube.com/watch?v=SsJqFe5\_Q1s](https://www.youtube.com/watch?v=SsJqFe5_Q1s)