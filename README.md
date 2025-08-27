# From-Composite-Identifiers-to-Staged-Trees
Neo4j demo for StageLift: compile order guards into the graph to simplify queries and cut latency. Builds a random Accounts+Transfers graph, constructs Stage nodes and TRANSFER_LIFT edges, and compares baseline vs lifted reachability for strictly increasing amounts.

# StageLift Neo4j Experiment

Compile strict-order guards *into* the graph and compare query latency vs. checking them at query time. We build an Accounts+Transfers graph, construct a lifted graph with `Stage(accId, level)` nodes and `TRANSFER_LIFT` edges, then measure baseline vs. lifted reachability for strictly increasing amounts.

## What’s here
- Cypher to: reset DB, create base graph, build StageLift, and run both queries
- A parameter sweep with K ∈ {10, 20, 30} background transfers
- Preliminary timings and speedups

## Requirements
- Neo4j 5.x (or Neo4j Sandbox) with APOC enabled
- Neo4j Browser (paste-and-run)
- Optional: use `PROFILE` to see plans (already included for build steps)

## Quick start
1. Open Neo4j Browser (sandbox or local).
2. Paste the script and run steps 0 → 5 in order.
3. To change density, edit Step 2:
   ```cypher
   // choose K: 10, 20, or 30
   UNWIND range(1, K) AS k
