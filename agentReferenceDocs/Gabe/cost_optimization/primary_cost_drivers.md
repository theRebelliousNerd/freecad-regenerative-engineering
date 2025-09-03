# Primary Cost Drivers in FDM Mass Production

Understanding the cost structure of FDM mass production is essential for making informed design decisions. The cost of a 3D printed part is primarily determined by three factors: print time, material usage, and labor.

## 1. Print Time (60-70% of Cost)
Print time is the single largest contributor to the cost of a 3D printed part. It is a direct measure of the amount of machine time required to produce the part, and it is influenced by several factors:

- **Z-Height**: The height of the part along the Z-axis is the most significant factor in determining print time. Each layer adds a fixed amount of time to the print, so reducing the Z-height is the most effective way to reduce print time.
- **Total Material Volume**: The total volume of material that needs to be extruded also affects print time. Larger, denser parts will take longer to print than smaller, lighter parts.
- **Movement Complexity**: The complexity of the toolpath can also impact print time. Parts with many small, intricate features will require more non-printing travel moves, which can add up to a significant amount of time.

## 2. Material Usage (20-25% of Cost)
The cost of the filament used to print the part is the second largest cost driver. This can be optimized through several design strategies:

- **Intelligent Infill**: Using an efficient infill pattern, such as gyroid or honeycomb, can provide the required strength with minimal material usage.
- **Lattice Structures**: For parts that require high stiffness with low weight, lattice structures can be used to reduce material consumption by 25-70%.
- **Efficient Orientation**: Orienting the part to minimize the need for support material can also lead to significant material savings.

## 3. Labor (5-15% of Cost)
Labor costs are associated with any manual intervention required in the production process. In a fully automated print farm, the goal is to reduce labor costs to near zero.

- **Support-Free Design**: Designing parts that are self-supporting eliminates the need for manual support removal, which is a significant labor cost.
- **Automated Ejection**: Automated part ejection systems eliminate the need for an operator to manually remove parts from the build plate.
- **Texture Integration**: Integrating a surface texture into the design can eliminate the need for manual post-processing to hide layer lines.
