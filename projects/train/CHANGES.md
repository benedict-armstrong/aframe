# Changelog

## Changes vs. `main`

### New Features

**Regression & Multi-Task Models**
- Added `SupervisedRegressionAframe` and `SupervisedMultiTaskAframe` model classes for parameter estimation alongside detection.
- Added reference configs for regression and multi-task training (`configs/regression/regression.yaml`, `configs/regression/multitask.yaml`).

**Waveform Parameter Propagation**
- Datasets now return injected waveform parameters (e.g. masses, spins) alongside strain data, enabling downstream use for regression targets.
- Updated waveform generators, loaders, and all supervised dataset classes to accept/return parameter batches.

**Arbitrary SNR Distributions**
- Added support for configurable SNR sampling distributions during training, replacing fixed SNR values.

**Per-Model Sample Rate Handling**
- Models can now declare an input sample rate; datasets will automatically resample data to match, enabling training across heterogeneous sample rates.

**S4D Architecture Improvements**

### Refactoring

- Model hierarchy reorganised: `AframeClassification` is now the base for `SupervisedAframe` and `Autoencoder`, with regression/multi-task classes building on top.
- `model/base.py` slimmed down; classification logic extracted to `model/classification.py`.
