# GRIDLINE — Game Design Overview (prototype v0.1)

**Genre:** cost-optimization / routing puzzle. **Platform:** offline browser (HTML Canvas + vanilla JavaScript). **Style:** monochrome hand-drawn engineering notebook.

## Premise

Connect substations A and B using an overhead line at the lowest possible in-game cost. Place towers on allowed grid cells and route wires from tower to tower. Terrain includes height variations, forests, costly private property, bodies of water and protected areas. The shortest route is not necessarily the cheapest.

## Core loop

Select one of three tower types → inspect placement and span legality → build tower and span → reach station B → compare your cost with the solver's result → retry to improve.

## Mechanics

- Low, medium and tall towers trade purchase/placement cost against span length and simulated clearance.
- Forests and private land can increase construction or crossing costs.
- Water and restricted cells cannot host towers; crossing them with a wire is possible only when the game's span rules allow it.
- Simplified sag and clearance calculations limit wire spans.
- Star rating compares player's cost with the optimizer's discrete minimum (3 stars at ≤115%; 2 at ≤145%; otherwise 1).
- 22 handcrafted levels, three tower types, undo/reset, best-route helper and local progress storage.

## Reference solver

Dijkstra's shortest-path algorithm is applied to a graph of legal tower-position/type states using the same cost and legality functions as the player. It finds a minimum-cost solution **within this simplified discrete game model**; that is not a real-world transmission-line design.

## Limits and future ideas

All tower heights, costs, sag, clearance and permissions are fictional/game-balanced. No real design, safety or regulatory compliance is implied. Potential improvements: level editor, branching networks, procedural levels and automated game-balance tests.
