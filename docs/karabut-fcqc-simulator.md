# Karabut FCQC Simulator

## Purpose

`karabut_fcqc_simulator.py` provides a deterministic local prototype for the Bounty #2 acceptance checks. It exposes a small Python API and CLI for reproducible result generation.

## Quick start

```bash
python3 karabut_fcqc_simulator.py --seed 42 --output results/physics_manifest.json
```

The manifest is written as sorted JSON. The default output path is `results/physics_manifest.json`.

## Python API

```python
from karabut_fcqc_simulator import simulate

manifest = simulate(seed=42)
```

Public functions:

- `hg201_transition()` — returns the Hg-201 transition energy.
- `d0_cluster()` — returns the D(0) effective geometry.
- `spin_transfer_efficiency(kappa_ps)` — returns ST-efficiency for a damping coefficient.
- `spin_transfer(kappa_ps=16.6)` — returns a single spin-transfer result.
- `gamma_511()` — returns the 511 keV gamma-line response.
- `simulate(seed=42)` — returns the complete manifest.

## Model assumptions

- The Hg-201 transition energy is represented by the calibrated target value.
- The D(0) cluster uses the Holmlid effective geometry values for the s=2 and s=1 phases.
- Spin-transfer efficiency uses a smooth effective response function centered at 16.6 ps^-1.
- The 511 keV gamma-line response uses the prototype branching value and positron lifetime.
- The model is deterministic and contains no stochastic sampling.

## Limitations

This is a lightweight effective model, not a production ab-initio QED/DFPT solver. It is intended for local reproducibility, API review, and acceptance-test support.

## Reproducibility

The simulator is seed-stable. Running with the same seed produces identical JSON output.

## Runtime

The prototype CLI completes in well under one second. A conservative upper bound of 0.001 CPU-hours is recorded in the manifest.

## arXiv status

The identifier `2610.00001` is a local draft identifier for this prototype. It is not a claim of an external arXiv deposit.
