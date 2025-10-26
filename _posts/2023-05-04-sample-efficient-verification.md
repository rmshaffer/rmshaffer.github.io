---
title: "Sample-efficient verification of continuously-parameterized quantum gates for small quantum processors"
categories:
  - Blog
tags:
  - paper
  - quantum computing
link: https://quantum-journal.org/papers/q-2023-05-04-997/
---

Most near-term quantum information processing devices will not be capable of implementing quantum error correction and the associated logical quantum gate set. Instead, quantum circuits will be implemented directly using the physical native gate set of the device. These native gates often have a parameterization (e.g., rotation angles) which provide the ability to perform a continuous range of operations. Verification of the correct operation of these gates across the allowable range of parameters is important for gaining confidence in the reliability of these devices. In this work, we demonstrate a procedure for sample-efficient verification of continuously-parameterized quantum gates for small quantum processors of up to approximately 10 qubits. This procedure involves generating random sequences of randomly-parameterized layers of gates chosen from the native gate set of the device, and then stochastically compiling an approximate inverse to this sequence such that executing the full sequence on the device should leave the system near its initial state. We show that fidelity estimates made via this technique have a lower variance than fidelity estimates made via cross-entropy benchmarking. This provides an experimentally-relevant advantage in sample efficiency when estimating the fidelity loss to some desired precision. We describe the experimental realization of this technique using continuously-parameterized quantum gate sets on a trapped-ion quantum processor from Sandia QSCOUT and a superconducting quantum processor from IBM Q, and we demonstrate the sample efficiency advantage of this technique both numerically and experimentally.
