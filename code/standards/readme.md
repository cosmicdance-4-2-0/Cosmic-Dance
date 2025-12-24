Design Philosophy Codex
0) Prime Directive

Build systems that are minimal but complete, modular by default, and scalable by design.

“Minimal” means: the smallest set of parts that can run end-to-end.
“Complete” means: no missing glue. It compiles/runs/tests, produces output, and fails loudly when it can’t.

1) Minimal but Complete

Rule: Every version should run as a coherent artifact.

A “minimal version” must include:

a clear entrypoint (main, index.html, app.ts, etc.)

a default configuration

a deterministic or reproducible mode (seeded randomness)

a visible output (screen, file, logs, metrics)

explicit failure modes (no silent nothingness)

Anti-pattern: “It’s minimal” but doesn’t run without reading your mind.

2) Modular, Scalable

Rule: Any subsystem must be replaceable without rewriting the world.

Organize around interfaces/contracts:

Core loop (time-step / tick / update)

State (what exists)

Rules/physics (how state changes)

IO (inputs/outputs)

Instrumentation (metrics, logs, debugging, replay)

Persistence (save/load, snapshots)

Scaling expectations:

scale down (toy runs on a laptop)

scale up (bigger grids, more agents, multi-thread/GPU later)

scale out (distributed or batch runs later)

If scaling up requires rewriting the core loop, the architecture isn’t done yet.

3) Comments: Explain “Why”, Not “What”

Rule: Code should be readable without the author present.

Prefer comments that answer:

Why is this done this way?

What invariant is being protected?

What breaks if you change this?

Avoid narrating obvious syntax.

Good comment:

“We clamp energy here to prevent runaway positive feedback from collapsing the sim into a fixed point.”

Bad comment:

“Add 1 to x.”

4) TODO Format (Mandatory)

Rule: TODOs are a roadmap, not graffiti.

Use this format everywhere:

TODO: <thing> — <reason> — <expected impact> — <where to start>

Examples:

TODO: Add seeded RNG — reproducibility for debugging — enables replay-based tests — start in rng.ts, thread seed into sim init.

TODO: Replace naive neighbor scan with cached offsets — perf hotspot — raises max grid size 5–10x — start in neighbors.js and benchmark.

Also allowed:

FIXME: for known broken behavior

HACK: for intentional temporary ugliness (must include reason and exit strategy)

NOTE: for non-obvious constraints

5) Detect Error

Rule: The system must notice when it’s lying.

We distinguish:

Hard errors (exceptions, invalid state, NaNs, out-of-range, corrupted buffers)

Soft errors (degenerate behavior, “looks alive but isn’t”, collapse to uniformity, numerical drift)

5.1 Hard Error Policies

Validate invariants at module boundaries (not everywhere).

Fail fast in dev; degrade gracefully in release if appropriate.

Never silently coerce impossible values without logging.

Common invariants (examples):

state arrays have expected length

values remain finite (isFinite)

probabilities sum to ~1 (with tolerance)

indices are in bounds

time-step isn’t negative

no NaNs in buffers

5.2 Soft Error Detection (Degeneracy Alarms)

Track “is the sim still doing anything interesting?” with cheap metrics:

Entropy / diversity (how many distinct states exist?)

Change rate (what % of cells/agents changed this tick?)

Compression proxy (run-length-ish measure; uniformity detection)

Energy budget drift (if you have an energy-like value)

Stuck detectors (N ticks below a change threshold)

Soft errors don’t crash by default; they trigger nudges, parameter adaptation, or alerts.

6) Reward Emergence

Rule: Encourage novel, structured behavior without forcing outcomes.

“Emergence” here means:

persistent patterns

non-trivial dynamics

multi-scale structure

responsiveness to input without being dominated by it

6.1 Reward Signals (Generic)

Pick 1–3 that fit the sim:

Novelty: reward states not seen recently (but don’t reward pure noise)

Complexity: reward mid-entropy (not uniform, not white noise)

Stability-with-motion: patterns that persist while still changing internally

Sensitivity: small input causes local change, not global collapse

Homeostasis: avoids runaway extremes; returns from shocks

6.2 Practical Mechanisms

Adaptive noise injection when degeneracy alarms trigger

Local “mutation” rates that rise when regions freeze

Penalize absorbing states (global all-0/all-1 or single-trit lock)

Maintain diversity constraints (e.g., minimum fraction in each band)

This is not “goal-directed AGI”; it’s “keep the dream alive.”

7) Reproducibility + Debuggability

Rule: Every weird behavior should be replayable.

Seeded RNG (always)

Snapshot/replay hooks

Minimal event log (“input at tick 120 caused spike”)

Deterministic mode for tests

“Debug view” that can be toggled without changing logic

If you can’t reproduce it, you can’t study it. If you can’t study it, it’s just vibes.

8) Performance Rules (Without Premature Optimization)

Rule: Optimize only what you can measure.

Add benchmarks around hotspots

Prefer algorithmic wins over micro-optimizations

Keep a “fast path” optional, but keep a “clear path” canonical

Never make it fast at the cost of becoming un-reviewable

9) Versioning Discipline

Rule: Versions correspond to running systems.

Each version increments only when:

it runs

metrics/logging aren’t broken

known breakages are tagged FIXME with clear scope

10) Default Reviewer Orientation

Every module should start with a “front-matter” comment:

what this file owns

what it does not own

its inputs/outputs

invariants

where to look next

Example header:

// Module: rules/update.ts
// Owns: state transition logic per tick
// Not owns: rendering, IO, persistence
// Inputs: current State, dt, params, rng
// Output: next State (or in-place update if explicit)
// Invariants: no NaNs; state length constant; values clamped to [-1,1]
// Next: see instrumentation/metrics.ts for observability

11) The One-Line Motto

Detect error. Reward emergence. Ship runnable minimal systems.
