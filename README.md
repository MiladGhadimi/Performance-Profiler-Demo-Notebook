# Quantum Performance Profiler (NISQ Execution Demo)

A compact demo tool that profiles **backend noise signatures** using diagnostic circuits and produces a simple
**execution recommendation** (backend + settings). It then benchmarks an algorithm suite and generates a
report comparing **baseline vs recommended** performance.

This project is designed to be easy to read, easy to extend, and useful as a starting point for
benchmark-driven execution tuning in near-term (NISQ) workflows.

---

## What it does

1. **Diagnostics (error signature)**
   - Estimates **readout error** (0→1 and 1→0) via preparation/measurement tests.
   - Estimates **depth sensitivity** by running increasing-depth circuits and fitting a decay trend.

2. **Recommendation (simple policy)**
   - Chooses a backend and a few execution knobs (e.g., transpiler optimization level, mitigation on/off).
   - Current policy is rule-based (intentionally simple), but the structure supports replacing it with
     Bayesian/ML tuning.

3. **Algorithm suite benchmark**
   - Runs representative circuits (e.g., GHZ, random, QAOA-like, and a small oracle-style toy circuit).
   - Produces a report: tables + plots + CSV summaries.

---

## Why this is useful

Different backends (real devices or simulators) have different gate sets, constraints, and noise behavior.
This demo shows a practical workflow:

**diagnose → summarize → decide → validate**

It’s a minimal “execution profiler” that can be extended to:
- additional diagnostics (2Q error sensitivity, crosstalk indicators),
- error mitigation strategies (readout mitigation, ZNE hooks),
- real cloud backends (IBM, IonQ, etc.),
- smarter tuning policies (Bayesian optimization / bandits).

---

## Project structure

