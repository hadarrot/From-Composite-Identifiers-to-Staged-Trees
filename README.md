# Leveled Graph — Neo4j Demo

Compile strict order guards *into* the graph so that increasing-amount path queries become simple reachability.  
This demo builds a random `Account`+`TRANSFER` graph, constructs a **leveled** graph with `Stage(accId, level)` nodes and `TRANSFER_LIFT` edges, and compares **baseline** vs **lifted** reachability for **strictly increasing amounts**.

---

## What this repo shows

- **Baseline query**: find paths in the original graph where transfer `amount`s are strictly increasing.
- **Lifted query**: run plain reachability in the compiled leveled graph, where the order constraint is encoded structurally.
- **Experiment script**: measure build times, per-run latencies, and timeouts across different edge counts; write a CSV report.

The leveled construction uses a special level **`-1`** to represent **⊥** (smaller than any amount).

