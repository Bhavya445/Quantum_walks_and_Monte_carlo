# Quantum Statistical Simulation and Noise Mitigation

## Project by
**Bhavya Sunkari**  
**Team Member:** Bhavya Sunkari – gst-Zw5kJBiWxcnCmgQ

---

## Overview
This project implements, optimizes, and analyzes a **Universal Statistical Simulator** based on the **Quantum Galton Board (QGB)** algorithm.  
The goal is to provide an **intuitive demonstration of quantum advantage**—in contrast to abstract algorithms like the Quantum Fourier Transform—by mapping quantum superposition to a familiar classical analogy: the Galton board.

In a classical board, balls cascade through pegs to form a normal distribution.  
In the quantum version, a single quantum state encodes all \( 2^n \) possible trajectories through an \( n \)-level board, using only **O(\(n^2\)) gates**.

---

## Features
- **Generalized QGB Implementation**: Build circuits for any number of layers in Qiskit.
- **Distribution Variants**:
  - Standard Hadamard coin → Binomial/Gaussian-like distribution.
  - Biased coin \(Ry(\theta)\) → Exponential distribution.
  - Grover coin → Distinct non-classical distribution.
- **Noise-Aware Optimization**:
  - Replaced non-native **C-SWAP (Fredkin)** gates with native gate decompositions (CNOT + CCX).
  - Tested on a realistic noise model (**FakeManila**) from IBM Quantum.

---

## Methodology
1. **Implementation**  
   Developed a parameterized QGB circuit generator in Qiskit. Validated correctness through noiseless simulations.

2. **Extension as a Universal Simulator**  
   - Modified the coin operator to produce different statistical distributions.
   - Demonstrated flexibility in simulating classical and non-classical outcomes.

3. **Noise Mitigation**  
   - Identified that transpilation of C-SWAP gates causes high gate counts and noise sensitivity.
   - Optimized by decomposing C-SWAP into native gates to reduce transpilation overhead.

4. **Evaluation**  
   - Compared unoptimized vs. optimized circuits.
   - Used **Hellinger distance** to measure closeness between noisy and ideal output distributions.
   - Optimized circuits showed significantly reduced error under noise.

---

## Results
- **Noiseless simulations** matched theoretical distributions exactly.
- **Under realistic noise**, optimized circuits consistently produced results closer to the ideal, confirming improved noise resilience.
- Demonstrated that hardware-aware circuit design is critical for achieving reliable quantum computation in the NISQ era.

---

## Tech Stack
- **Quantum Framework**: Qiskit
- **Backend Simulation**: IBM Quantum FakeManila
- **Noise Models**: Real hardware noise data
- **Metrics**: Hellinger distance

---

## References
- [Quantum Galton Board Research Paper](https://arxiv.org/abs/2202.01735) 
- [IBM Quantum Qiskit Documentation](https://qiskit.org/)

---

## Project Presentation
[View Presentation Deck](https://docs.google.com/presentation/d/16-2bTE0rXkLQCJPCYKkfUfEXlrRamiTdLnY03DuV2kU/edit?usp=sharing)
