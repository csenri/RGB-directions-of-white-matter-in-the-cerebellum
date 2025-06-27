# RGB-directions-of-white-matter-in-the-cerebellum
# Multi-Scale Anisotropy Analysis in 3D White Matter MRI

This project focuses on the extraction and characterization of local anisotropy patterns in 3D brain MRI volumes, specifically within white matter regions. We implement a multi-scale image processing pipeline that leverages second-order differential structures (Laplacian, Hessian, and Structure Tensor) to analyze voxel-wise directional properties.

##  Overview

We aim to compute meaningful features that describe the **scale-dependent orientation and anisotropy** of tissue structures. These features are especially relevant in white matter, where the fiber organization plays a key role.

The pipeline is implemented in Python using `NumPy` and `SciPy`, and includes:

- Laplacian computation via second-order Gaussian derivatives  
- Structure tensor analysis to estimate local orientation  
- Hessian eigendecomposition and computation of **Fractional Anisotropy (FA)**  
- Multi-scale approach to capture structures of varying size (e.g., blobs, vessels, fibers)

---

##  Features Extracted

###  Laplacian of Gaussian (LoG)
Captures isotropic blob-like structures and intensity curvature.  
Used to detect local maxima in scale-space and identify spherical patterns.

###  Structure Tensor (2D)
Estimates the dominant direction and degree of anisotropy in the image plane.  
Eigenvalues and eigenvectors are computed for each voxel to characterize local orientation.

### ✅Fractional Anisotropy (FA) from Hessian (3D)
Uses eigenvalues of the Hessian matrix to quantify directional variation in all 3 spatial dimensions.  
Values are clamped to [0, 1], where:
- FA ≈ 0 → isotropic region (blob or flat)
- FA ≈ 1 → anisotropic region (fiber or edge-like)
