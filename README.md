#  Protein Conformation Generation using Variational Autoencoder (VAE)

**Author:** [Vikash Kumar](https://github.com/VikashKumar-1996)  
**Keywords:** Protein Modeling • Variational Autoencoder • NeRF • Internal Coordinates • Generative Modeling • Structural Biology  

---

##  Overview
This project demonstrates a **deep generative modeling approach** to predict and generate intermediate **protein conformations** between known *open* and *closed* states.  

Using a **β-VAE (Variational Autoencoder)** trained on **internal coordinates** (bond lengths, bond angles, torsion angles), this framework learns a compact **latent representation** of protein conformational space.  
The decoder reconstructs **3D Cartesian coordinates** using a **NeRF-based algorithm**, enabling visualization and physical validation of generated structures.

---

##  Motivation
Proteins exhibit conformational flexibility essential for biological function.  
Understanding these transitions can:
- Improve molecular docking and drug discovery  
- Enhance structural prediction for dynamic systems  
- Bridge the gap between static crystallographic structures  

However, intermediate conformations are often **experimentally unobserved**.  
This project aims to **learn a continuous conformational manifold** from open and closed state data, allowing interpolation and sampling of plausible intermediates.

---

##  Methodology

###  1. Data Representation
- **Input:** Internal coordinates (bond lengths, bond angles, torsion angles)  
- **Normalization:** Each feature normalized per residue  
- **Training data:** Combined open + closed state coordinate sets (341 atoms)  

###  2. Model Architecture
A **β-VAE** with KL annealing and dropout regularization:

```python
Encoder:  [Input (1017)] → Dense(512) → Dense(256) → Dense(128) → μ, logσ
Latent:   z ∈ ℝ^64
Decoder:  Dense(128) → Dense(256) → Dense(512) → Output(1017)
