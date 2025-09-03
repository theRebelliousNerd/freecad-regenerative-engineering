# 2.1. The Unreliability of Slicer-Generated Supports

Slicer-generated supports, while useful for one-off prototypes, are a significant liability in a print farm environment for several reasons:

* **Inconsistency:** The algorithms that generate supports can produce slightly different results based on minor changes in model orientation or slicer version, leading to a lack of process repeatability.
* **Print Failures:** Dense, complex support structures can detach from the build plate or collide with the nozzle, causing print failures that are costly at scale.
* **Surface Damage:** The points where supports touch the model inevitably leave behind scarring and blemishes. Removing these marks requires manual post-processing (sanding, filing), which is a labor-intensive and non-scalable activity.
* **Labor Cost:** The act of breaking away and cleaning up auto-generated supports is one of the most significant labor costs in an FDM production workflow.

For a part to be viable for automated, mass production, it must be designed to either require no support at all or to use custom, integrated supports that are engineered for clean, effortless, and repeatable removal.
