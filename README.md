# Synthetic-Image-Detection-using-Gradient-Fields

# Synthetic Image Detection using Gradient Fields

An interpretable computer vision project for lightweight synthetic image analysis using luminance gradients, covariance structure, and PCA-based visualization.

## Overview

As generative image models become increasingly photorealistic, distinguishing synthetic images from real photographs is no longer a trivial visual task. This project explores a lightweight, interpretable alternative to black-box classification by analyzing the structure of image gradient fields.

Instead of relying on metadata, deep classifiers, or proprietary forensic pipelines, this notebook investigates whether simple first-order image statistics can reveal meaningful differences between authentic photographs and AI-generated images.

The core idea is straightforward:

- convert an RGB image to luminance
- compute spatial gradients
- construct a gradient-field covariance matrix
- analyze its principal directions with PCA
- derive interpretable statistics from the resulting structure
- produce a heuristic authenticity assessment

The result is a compact and visually intuitive workflow for exploring image authenticity through gradient geometry.

## Why this project is interesting

Modern diffusion-generated images often appear realistic at a glance, but their local high-frequency structure can differ from that of camera-captured photographs. Real images tend to exhibit gradient patterns shaped by optics, lighting, materials, and sensor physics, while synthetic images may produce more isotropic, unstable, or over-textured gradient behavior.

This project turns that observation into an analytical pipeline that is:

- **interpretable** rather than opaque
- **lightweight** and easy to run
- **visual**, with PCA-based gradient projections
- **extensible** into a more formal forensic detector

Rather than treating authenticity detection as a pure classification problem, this notebook frames it as a structured signal-analysis problem.

## Method

Given an input image, the pipeline performs the following steps:

1. **RGB to luminance conversion**  
   The image is converted to a perceptually weighted luminance channel.

2. **Gradient computation**  
   Spatial gradients are computed in the x and y directions.

3. **Gradient matrix construction**  
   The per-pixel gradients are flattened into a 2D matrix of gradient vectors.

4. **Covariance analysis**  
   A gradient covariance matrix is built to summarize the global directional structure of the image.

5. **Eigen-analysis / PCA**  
   Principal directions and eigenvalues are extracted to characterize anisotropy, directional coherence, and energy distribution.

6. **Heuristic scoring**  
   Interpretable statistics such as anisotropy, principal ratio, trace, determinant, and cross-correlation are combined into a lightweight heuristic score.

7. **Visualization**  
   The notebook generates an infographic-style output containing:
   - the original image
   - a gradient magnitude rendering
   - a PCA-style projection of the gradient field with principal component overlays

## Features

- Upload and analyze any image directly in Google Colab
- Compute luminance-based spatial gradients
- Build and inspect gradient covariance structure
- Visualize gradient-field geometry with PCA
- Produce a heuristic prediction:
  - `LIKELY REAL`
  - `LIKELY FAKE`
  - `AMBIGUOUS`
- Display interpretable summary statistics for further inspection

## Example outputs

The notebook produces both visual and numerical outputs, including:

- authenticity label
- heuristic fake score
- anisotropy
- principal eigenvalue ratio
- covariance trace
- determinant
- full gradient covariance matrix

This makes the project useful both as a demonstration tool and as a starting point for more rigorous experimentation.
