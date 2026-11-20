# Agent architecture and quality gates

Use one shared object model across analysis, geometry, execution, and review. A major object should retain an ID, type, floor or site zone, layer, geometry, dimensions or area when known, level, relations, edit protection, source, and verification state.

Build relations for room adjacency, room to corridor, room to door, stair between floors, column to wall, building to site, road to entrance, and landscape node to path. Do not classify intersections as errors without considering the object types and intended connection.

Classify findings before repair.

- A-level findings can be repaired when their intent is unambiguous, such as duplicate geometry, zero-length objects, and confirmed layer or text-style mistakes.
- B-level findings require geometric and architectural analysis before repair, such as wall gaps, annotation conflicts, door connections, and boundary errors.
- C-level findings require design review, such as entrance relocation, structural-grid changes, fire strategy, building outline, floor count, height, or major site-level changes.

Use the closed loop design, draw, inspect, classify, repair, recheck, viewport-review, and deliver. Preserve the source file and use a new working copy. A successful command or MCP response is not evidence that the drawing is correct.

For unresolved code, fire, structure, accessibility, or planning issues, report the applicable source and mark the item pending review. Do not claim full compliance from automated checks alone.

