---
title: "Surrogate-based optimization for variational quantum algorithms"
categories:
  - Blog
tags:
  - paper
  - quantum algorithms
link: https://journals.aps.org/pra/abstract/10.1103/PhysRevA.107.032415
---

Variational quantum algorithms are a class of techniques intended to be used on near-term quantum computers. The goal of these algorithms is to perform large quantum computations by breaking the problem down into a large number of shallow quantum circuits, complemented by classical optimization and feedback between each circuit execution. One path for improving the performance of these algorithms is to enhance the classical optimization technique. Given the relative ease and abundance of classical computing resources, there is ample opportunity to do so. In this work, we introduce the idea of learning surrogate models for variational circuits using a few experimental measurements, and then performing parameter optimization using these models as opposed to the original data. We demonstrate this idea using a surrogate model based on kernel approximations, through which we reconstruct local patches of variational cost functions using batches of noisy quantum circuit results. Through application to the quantum approximate optimization algorithm and preparation of ground states for molecules, we demonstrate the superiority of surrogate-based optimization over commonly used optimization techniques for variational algorithms.
