# Protein-Conformation-Generation-using-Variational-Autoencoder-

##  Project Overview

Proteins adopt complex 3D conformations that determine their function. Modeling and generating these structures is a central problem in computational biology. This project:

- Learns protein structures using **bond lengths, bond angles, and torsion angles**.
- Incorporates **contact maps** and **Gaussian distance priors** to enforce structural constraints.
- Encodes protein conformations into a **32-dimensional latent space**.
- Generates novel protein conformations and reconstructs them into **3D Cartesian coordinates** using a **NeRF-based algorithm**.

---

##  Features

- **Variational Autoencoder (VAE)** for protein internal coordinates.
- **NeRF-based 3D reconstruction** ensuring correct geometry.
- **Physical constraints**: contact map and Gaussian distance regularization.
- **Loss functions** include:
  - Reconstruction loss on internal coordinates
  - KL divergence for latent space regularization
  - Cartesian coordinate consistency loss
  - Contact map binary cross-entropy loss
  - Gaussian distance regularization loss
- **Post-processing**:
  - Alignment to reference structure using Kabsch algorithm
  - RMSD evaluation
  - Exporting conformations as multi-model PDB files
