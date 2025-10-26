---
title: "Quantum-Classical Auxiliary Field Quantum Monte Carlo with Matchgate Shadows on Trapped Ion Quantum Computers"
categories:
  - Blog
tags:
  - paper
  - quantum chemistry
link: https://arxiv.org/abs/2506.22408
---

We demonstrate an end-to-end workflow to model chemical reaction barriers with the quantum-classical auxiliary field quantum Monte Carlo (QC-AFQMC) algorithm with quantum tomography using matchgate shadows. The workflow operates within an accelerated quantum supercomputing environment with the IonQ Forte quantum computer and NVIDIA GPUs on Amazon Web Services. We present several algorithmic innovations and an efficient GPU-accelerated execution, which achieves a several orders of magnitude speedup over the state-of-the-art implementation of QC-AFQMC. We apply the algorithm to simulate the oxidative addition step of the nickel-catalyzed Suzuki-Miyaura reaction using 24 qubits of IonQ Forte with 16 qubits used to represent the trial state, plus 8 additional ancilla qubits for error mitigation, resulting in the largest QC-AFQMC with matchgate shadow experiments ever performed on quantum hardware. We achieve a 9x speedup in collecting matchgate circuit measurements, and our distributed-parallel post-processing implementation attains a 656x time-to-solution improvement over the prior state-of-the-art. Chemical reaction barriers for the model reaction evaluated with active-space QC-AFQMC are within the uncertainty interval of +/- 4 kcal/mol from the reference CCSD(T) result when matchgates are sampled on the ideal simulator and within 10 kcal/mol from reference when measured on QPU. This work marks a step towards practical quantum chemistry simulations on quantum devices while identifying several opportunities for further development.
