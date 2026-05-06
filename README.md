Voici un `README.md` complet dans le même style :

````markdown
# Quantum Phase Estimation

<p align="center">
  <img src="https://img.shields.io/badge/Quantum%20Computing-Phase%20Estimation-blueviolet?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white" />
</p>

<p align="center">
  <b>Implementation and analysis of the Quantum Phase Estimation algorithm.</b>
</p>

---

## Overview

This repository contains a practical implementation of the **Quantum Phase Estimation** algorithm, one of the fundamental algorithms in quantum computing.

Quantum Phase Estimation, often abbreviated as **QPE**, is a central subroutine used to estimate the eigenphase associated with an eigenvector of a unitary operator. It plays a key role in many major quantum algorithms, including Shor's algorithm, quantum simulation, amplitude estimation, and eigenvalue estimation problems.

The project is structured around Jupyter notebooks that introduce the theoretical background, construct the corresponding quantum circuits, and explore the behavior of the algorithm through concrete implementations.

---

## Repository Content

```text
QuantumPhaseEstimation/
│
├── QComp-QPE.ipynb              # Quantum computing notebook on phase estimation
├── QPE-Implementation.ipynb     # Main implementation notebook
├── README.md                    # Project documentation
└── .gitignore
````

---

## Topics Covered

This repository explores several key notions in quantum computing:

* Quantum Phase Estimation
* Eigenvalues and eigenvectors of unitary operators
* Controlled unitary operations
* Quantum Fourier Transform
* Inverse Quantum Fourier Transform
* Phase kickback
* Quantum measurement
* Binary representation of phases
* Circuit construction
* Simulation of quantum circuits
* Interpretation of measurement outcomes

---

## Main Notebooks

The repository contains two main notebooks:

```text
QComp-QPE.ipynb
```

and

```text
QPE-Implementation.ipynb
```

These notebooks contain the full practical work, including:

* theoretical explanation of Quantum Phase Estimation;
* construction of the QPE circuit;
* implementation of controlled unitary operations;
* use of the inverse Quantum Fourier Transform;
* simulation of quantum states;
* interpretation of the final measurement results.

---

## Installation

First, clone the repository:

```bash
git clone https://github.com/karimelhoudaigui/QuantumPhaseEstimation.git
cd QuantumPhaseEstimation
```

Then create a virtual environment:

```bash
python -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

On Windows:

```bash
.venv\Scripts\activate
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

If no `requirements.txt` file is provided, install the common dependencies manually:

```bash
pip install numpy matplotlib jupyter qiskit
```

---

## Run the Notebooks

Launch Jupyter:

```bash
jupyter notebook
```

Then open one of the notebooks:

```text
QComp-QPE.ipynb
```

or

```text
QPE-Implementation.ipynb
```

You can also use JupyterLab:

```bash
jupyter lab
```

---

## Project Goal

The goal of this project is to understand how a quantum computer can estimate the phase associated with an eigenvalue of a unitary operator.

Given a unitary operator (U), suppose that (|\psi\rangle) is an eigenvector of (U). Then:

```math
U|\psi\rangle = e^{2\pi i \theta}|\psi\rangle
```

where:

```math
\theta \in [0,1)
```

The objective of Quantum Phase Estimation is to estimate the value of (\theta) using a quantum circuit.

This phase contains information about the eigenvalue of the unitary operator, and in many applications this allows one to extract spectral information about a physical or mathematical system.

---

## Mathematical Idea

Quantum Phase Estimation uses two quantum registers.

The first register stores an approximation of the phase:

```math
|\theta\rangle
```

The second register contains an eigenstate of the unitary operator:

```math
|\psi\rangle
```

The algorithm starts from the state:

```math
|0\rangle^{\otimes t}|\psi\rangle
```

After applying Hadamard gates to the first register, the state becomes:

```math
\frac{1}{2^{t/2}} \sum_{k=0}^{2^t-1} |k\rangle |\psi\rangle
```

Then controlled powers of the unitary operator are applied:

```math
CU^{2^j}
```

Using the eigenvalue relation,

```math
U^{k}|\psi\rangle = e^{2\pi i k \theta}|\psi\rangle
```

the global state becomes:

```math
\frac{1}{2^{t/2}} \sum_{k=0}^{2^t-1} e^{2\pi i k \theta}|k\rangle |\psi\rangle
```

The phase is now encoded in the amplitudes of the first register.

Applying the inverse Quantum Fourier Transform extracts this phase into the computational basis:

```math
QFT^{-1}
```

The final measurement gives an integer (m) such that:

```math
\theta \approx \frac{m}{2^t}
```

where (t) is the number of counting qubits.

---

## Physical Interpretation

The Quantum Phase Estimation algorithm can be interpreted as an interference experiment.

The controlled powers of the unitary operator create phase differences between the computational basis states of the counting register. These relative phases are not directly observable at first, but the inverse Quantum Fourier Transform converts them into measurable probabilities.

In this sense, QPE transforms hidden phase information into classical measurement outcomes.

Physically, if the unitary operator is generated by a Hamiltonian (H), one may write:

```math
U = e^{-iHt}
```

If (|\psi\rangle) is an eigenstate of (H), then:

```math
H|\psi\rangle = E|\psi\rangle
```

and therefore:

```math
U|\psi\rangle = e^{-iEt}|\psi\rangle
```

Estimating the phase of (U) is then directly related to estimating the energy (E) of the physical system.

This is why Quantum Phase Estimation is a fundamental tool in quantum simulation and quantum chemistry.

---

## Algorithm Structure

The standard QPE circuit follows these steps:

1. Prepare the counting register in the state:

```math
|0\rangle^{\otimes t}
```

2. Prepare the second register in an eigenstate:

```math
|\psi\rangle
```

3. Apply Hadamard gates to the counting register:

```math
H^{\otimes t}
```

4. Apply controlled powers of the unitary operator:

```math
CU^{1}, CU^{2}, CU^{4}, \dots, CU^{2^{t-1}}
```

5. Apply the inverse Quantum Fourier Transform:

```math
QFT^{-1}
```

6. Measure the counting register.

The result gives a binary approximation of the phase (\theta).

---

## Example

If the phase has an exact binary expansion using (t) bits,

```math
\theta = 0.\theta_1\theta_2\dots\theta_t
```

then the measurement returns the bit string:

```math
\theta_1\theta_2\dots\theta_t
```

which corresponds to the integer:

```math
m = 2^t \theta
```

Therefore:

```math
\theta = \frac{m}{2^t}
```

When the phase cannot be represented exactly with (t) bits, the algorithm returns the closest approximation with high probability.

---

## Skills Practiced

Through this project, you will practice:

* implementing a fundamental quantum algorithm;
* constructing controlled unitary operations;
* using the Quantum Fourier Transform;
* understanding phase kickback;
* interpreting quantum measurement results;
* connecting unitary eigenvalues with measurable phases;
* simulating quantum circuits in Python;
* relating quantum algorithms to spectral estimation problems.

---

## Applications

Quantum Phase Estimation is a central building block in many quantum algorithms, including:

* Shor's factoring algorithm;
* quantum simulation;
* quantum chemistry;
* Hamiltonian eigenvalue estimation;
* amplitude estimation;
* order finding;
* algorithms based on spectral decomposition.

Its importance comes from the fact that many physical and computational problems can be reformulated as eigenvalue estimation problems.

---

## Technologies

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white" />
  <img src="https://img.shields.io/badge/Qiskit-6929C4?style=flat-square" />
  <img src="https://img.shields.io/badge/Quantum%20Computing-6A0DAD?style=flat-square" />
</p>

---

## Author

**Karim EL HOUDAIGUI**

Double-degree engineering background in **High-Performance Computing** and **Quantum Information**, with interests in numerical simulation, quantum computing, quantum foundations and scientific computing.

Website: [elhoudaiguimath.com](https://elhoudaiguimath.com)

---

## License

This repository is intended for educational and research purposes.

You may adapt the material for learning, teaching or experimentation, provided that proper credit is given.

---

<p align="center">
  <b>Estimating quantum phases to reveal the spectrum of unitary evolution.</b>
</p>
```
