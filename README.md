# QComp - Coding Session #1: Implementing QPE

This repository contains the implementation of the Quantum Phase Estimation (QPE) algorithm as part of the QComp lab sessions. This session focuses on implementing and analyzing the HHL algorithm, starting with QPE.

## Overview

This Jupyter notebook implements the Quantum Phase Estimation algorithm using Qiskit. It covers:

1. **Entangled States**: Generating entangled states over n qubits.
2. **QPE Implementation**: Building the QPE circuit for estimating eigenvalues.
3. **Exact Results**: Testing QPE with exact fractions.
4. **Approximate Results**: Handling irrational phases like 1/3.
5. **Superposition**: QPE with superpositions of eigenvectors.

## Prerequisites

To run this notebook, you need:

- Python 3.x
- Qiskit
- Qiskit Aer
- NumPy
- Matplotlib
- SciPy

Install the required packages using pip:

```bash
pip install numpy matplotlib qiskit qiskit-aer scipy
```

## Structure

The notebook is divided into sections:

### 0 - Before anything else
Checks the introductory notebook Qcomp-TP-0-Intro-QisKit.

### 1 - Small practice
Implements a function to create entangled states |00...0> + |11...1> over n qubits.

### 2 - QPE
- **Math questions**: Explains the unitary operator U with phase 6/8.
- **Implementation**: Builds the QPE circuit with size_eig bits of precision.
- **Exact results**: Tests with different fractions (0/8 to 7/8) and precisions.
- **Approximate results**: Tests with 1/3, showing how QPE approximates irrational phases.
- **Superposition**: Handles superpositions of eigenvectors.

## Key Functions

- `entangledState(n)`: Creates an entangled state over n qubits.
- `QPE(U, size_eig=3, endMeasure=False)`: Implements QPE for unitary U.
- `QPEotherPhi(U, size_eig=3, endMeasure=False)`: QPE with superposition initialization.
- `U(frac)`: Creates a unitary with phase frac.
- `V(frac1, frac2)`: Creates a unitary with two phases.

## Results

The notebook demonstrates:

- Correct estimation of exact fractions with sufficient precision.
- Approximation of irrational numbers like 1/3.
- Handling of superpositions, showing peaks for each eigenvalue.

## Usage

Run the notebook cells in order. The code includes:

- Library installations (may need to run separately).
- Utility functions for bit manipulation and state printing.
- Circuit constructions and simulations.
- Plots of measurement distributions.

## Notes

- The notebook uses Qiskit's AerSimulator for simulations.
- Outputs include state vectors, measurement counts, and plots.
- For large n, simulations may take time.

## References

- Qiskit documentation: https://qiskit.org/
- Quantum Phase Estimation: Nielsen & Chuang, "Quantum Computation and Quantum Information"

## Author

Karim El Houdaigui

## License

This project is for educational purposes.