- Set your Top Thickness to 0.  It can be 3-4 layers, but the default 0.8mm thickness HUGELY increases slicing time
- Most of us do 1 perimeter, 999 bottom layers and 2-3 top layers with 0 Top Thickness
- For a nice, thick print, do 0.48 min depth and set the bottom three layers to 0.16mm and then 0.04 from there. Saves about 30 minutes
	- the first 3 layers do height of .16 and then drop to .04 with base layer .16 with a height range modifier on the model
- Ensure vertical shell thickness - This setting adds extra infill along sloping walls to prevent gaps from being visible, CPU intensive to calculate and entirely unnecessary because we're printing at 100% infill 
- Detect overhang perimeters/Slow down for overhangs - Another CPU intensive setting that shouldn't be necessary at all since HueForge shouldn't be creating any overhangs
- Reduce infill retraction - Another CPU intensive setting which can result in visible scarring over solid infill regions, this should be turned off for HueForge prints regardless of the CPU impact imo


BEST PRINT SIZE
- about 175 x 245 (5:7 ratio) (portrait)