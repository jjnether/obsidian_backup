Banned Characters:
- …
- —
- –
- “
- ”

type `tmm 1` t toggle map markers

## Helpful for Navmesh

| Name                      | Hotkey      | Description                                                              |
| ------------------------- | ----------- | ------------------------------------------------------------------------ |
| Top View                  | **T**       | Force a top-down view.                                                   |
| Toggle Collision Geometry | **F4**      | Toggles collision geometry on/off.                                       |
| Toggle Hidden             | **1**       | Makes the current selection visible/translucent/invisible in the editor. |
| Unhide All                | **Alt+1**   | Unhides all hidden objects.                                              |
| Refresh                   | **F5**      | Refreshes the current cell and unhides all hidden objects.               |
| Toggle Toggle Water       | **Shift+W** | Toggles Water on/off.                                                    |
| Toggle Cell Borders       | **B**       | In the Exterior, toggles Cell Borders on/off.                            |

## Navmesh Specific

| Name               | Hotkey       | Description                                                                     |
| ------------------ | ------------ | ------------------------------------------------------------------------------- |
| Navmesh            | **Ctrl+E**   | Enter navmesh mode.                                                             |
| View Mode          | **W**        | Alternate between standard/on top/navmesh only view modes.                      |
| Delete             | **R**        | Delete selected object.                                                         |
| Triangles          | **T**        | Allows selection of triangles.                                                  |
| Vertices           | **V**        | Allows selection of vertices.                                                   |
| Edges              | **G**        | Allows selection of edges.                                                      |
| New Vertex         | **RMB**      | Creates a new vertex. (can also create vertex on an edge when hovering over it) |
| Merge Vertices     | **Q**        | Merges selected vertices (merges to the first vertex selected).                 |
| New Triangle       | **A**        | Create triangle (from selected vertices).                                       |
| New Triangle       | **Ctrl+RMB** | Create triangle (from two selected vertices).                                   |
| Vertex Swap        | **Tab**      | Swaps which vertices are selected in the triangle.                              |
| Edge Swap          | **S**        | Swaps the edge position                                                         |
| Drop to Ground     | **F**        | Drops the selected object (vertex) to the nearest surface.                      |
| Flood Fill         | **F**        | Selects entire navmesh connected to selected triangle.                          |
| Inverse Flood Fill | **I**        | Selects every navmesh not connected to the selected triangle.                   |
| Preferred Pathing  | **P**        | Toggle preferred pathing for selected triangles.                                |
| Water              | **O**        | Toggle water for selected triangles.                                            |
| Find Cover         | **Ctrl+F2**  | Finds cover edges for current cell (easier to see if `draw cover` is enabled).  |
| Finalize Navmesh   | **Ctrl+F3**  | Finalizes current cell's navmeshes.                                             |
| Find Triangle      | **Ctrl+F**   | Finds triangles (can use to check navmesh and move through warnings).           |

- Double left click on an edge to select its two vertices
	- You can double left click an edge, hold ctrl, then double left click another edge to create a triangle between the two edges


Exterior Auto-generated Navmesh Settings:
![[Pasted image 20250322103607.png]]