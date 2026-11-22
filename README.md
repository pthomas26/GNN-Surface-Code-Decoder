# GNN Decoder for the Surface Code

**A graph neural network decoder benchmarked against minimum-weight perfect matching under circuit-level noise**

Fault-tolerant quantum computing relies on a *decoder*: an algorithm that reads the syndrome measured on a quantum error-correcting code and infers which correction to apply, fast enough to keep up with the hardware. This project simulates the rotated surface code, establishes the standard matching baseline, and trains a neural decoder against it.

## Part 1: Threshold with MWPM

- **Simulation:** rotated surface-code memory experiments with [Stim](https://github.com/quantumlib/Stim), for code distances d = 3 to 7 under circuit-level depolarizing noise.
- **Decoding:** minimum-weight perfect matching (MWPM) on the detector error model, using [PyMatching](https://github.com/oscarhiggott/PyMatching).
- **Evaluation:** logical error rates estimated by Monte Carlo sampling.

**Results**

- Threshold located at **~1.2%** physical error rate.
- Error-suppression factor of **~5** below threshold: the logical error rate drops by about 5x each time the distance increases by 2.

## Part 2: Graph neural network decoder

- **Model:** a graph neural network decoder in PyTorch, trained on **30M+ syndromes** generated with Stim under the same circuit-level noise.
- **Baselines:** MWPM and correlated MWPM, evaluated on identical test sets.
- **Metric:** logical error rate.

**Results**

- At **d = 3**, the GNN decoder cuts the logical error rate by **10–17%** relative to the matching baselines.
- At **d = 5**, the gap to the baselines was quantified as the main target for improvement.
- Per-syndrome inference latency was measured as the target for real-time decoding.

## Run it

```bash
pip install stim pymatching torch numpy matplotlib
```

Then open the notebooks and run all cells.

## Stack

Python · Stim · PyMatching · PyTorch · NumPy · Matplotlib
