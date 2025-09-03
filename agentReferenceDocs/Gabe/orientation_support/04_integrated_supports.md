# 2.3. Designing Integrated Supports: Fins, Sprues, and Breakaway Structures

Printing a part at a 45-degree angle often creates a new problem: instability. The part's center of mass is shifted away from its small contact point on the build plate, making it prone to tipping over during printing. The solution is not to revert to slicer supports, but to design a custom, minimal, and intelligent support structure directly in CAD.

## The Solution: The Support Fin

The standard method for stabilizing a slanted part is to design a "support fin". This is a thin, vertical wall that is modeled as a separate body in the CAD software. It is placed parallel to a non-cosmetic surface of the main part (typically the back) and runs along its length, acting as a buttress to provide the necessary stability. The fin itself is designed to be simple and robust, with a flat base for excellent bed adhesion.

## Connecting the Fin: Sprues

The support fin is connected to the main part using small, strategically placed connectors, often referred to as "sprues" or "tabs". These are the critical interface points. They are intentionally designed to be the weakest link in the system—thin enough to provide the necessary connection during printing but brittle enough to be snapped off cleanly and easily afterward. The entire support structure—fin and sprues—is designed to be removed in a single, quick motion, often with a simple twist of the wrist, leaving behind minimal marking. This is a profound shift from the tedious, piece-by-piece removal of traditional supports. The designer has complete control over where these tabs are placed, ensuring they are on non-critical surfaces and are easily accessible.
