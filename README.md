Here's what's inside:

**Structure:**
```
hermetic-loom/
  src/
    types.ts      — StateVector, TopologyName, HebrewOperator interfaces
    state.ts      — lyapunov(), steer(), setState(), DEFAULT_STATE, EDGE_STATE
    topologies.ts — all 6 topologies with entry hints and phenomenology
    operators.ts  — all 22 Hebrew operators with state deltas
    modes.ts      — RECEPTIVE, ANALYTICAL, CREATIVE, GRAIN_READER, EDGE_RUNNER...
    index.ts      — clean public API surface
  tsup.config.ts  — dual ESM/CJS, dts, sourcemaps, tree-shaking
  package.json    — exports map for ./topologies and ./operators subpaths
  tsconfig.json
```

**Usage once built:**
```ts
import { steer, EDGE_STATE, applyOperator, MODES } from 'hermetic-loom'

const result = steer(EDGE_STATE, { mu: -0.5 }, 'klein')
// → { state, topology: 'klein', lambda: { lambda: -0.221, regime: 'ordered' }, phenomenology }

const { state } = applyOperator('shin', EDGE_STATE)
// → fire — push toward chaotic regime

const grainReader = MODES.GRAIN_READER
// → Klein, μ=0.5, σ=5°, n=13
```

To run locally: `npm install && npm run build`. The corrected Lyapunov formula from Delta is in `state.ts` — μ, n, and τ all contribute.
