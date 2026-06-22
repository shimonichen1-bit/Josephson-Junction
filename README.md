# Josephson Effects - Data Analysis

## Overview
This repository contains the Python scripts used to process, filter, and analyze experimental data for the investigation of the DC and AC Josephson effects in Niobium point-contact junctions, as well as the superfluid phase transition of liquid helium.

## Data Analysis Pipeline
The core functionality of this project lies in its multi-stage signal processing pipeline, which was developed to mitigate heavy high-frequency experimental noise and extract accurate physical parameters directly from raw data:

* **Noise Reduction & Filtering:** The pipeline uses Savitzky-Golay smoothing filters on raw derivative data ($dV/dI$). This isolates clear physical transitions while preserving the underlying peak positions and preventing artifacts from the noise-reduction process.
* **Critical Current Extraction ($I_c$):** The scripts locate the positive and negative transition boundaries where the junction shifts from a zero-resistance supercurrent state to a resistive state. A Gaussian fitting procedure is applied to each peak to systematically evaluate thermal and electronic broadening, using the peak width as an error estimator.
* **Shapiro Steps & Flux Quantum Approximation ($\Phi_0$):** The code reconstructs the baseline current-voltage (I-V) characteristics through numerical integration. It applies a local maxima detection algorithm with automated prominence thresholds to identify the quantized voltage steps under RF radiation, followed by a linear regression against the step indices to calculate the experimental magnetic flux quantum.
* **Thermal Phase Transition Mapping:** To evaluate the cryogenic environment, the pipeline processes helium temperature logs over time. It calculates the second derivative of the warming rate ($\frac{d^2T}{dt^2} = 0$) to locate the exact mathematical inflection point corresponding to the lambda point ($T_\lambda$) transition.


