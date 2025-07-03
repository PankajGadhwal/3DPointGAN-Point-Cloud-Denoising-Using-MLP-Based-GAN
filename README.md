# 3DPointGAN: Point Cloud Denoising Using MLP-Based GAN


## Overview

3DPointGAN is a deep learning framework designed for denoising 3D point clouds using a Generative Adversarial Network (GAN). It aims to restore clean, high-quality point clouds from noisy inputs while preserving the underlying geometric structure.

Point cloud data, commonly used in 3D scanning and perception tasks, often suffers from sensor noise. Traditional denoising methods like local surface fitting or statistical filters struggle with complex or non-uniform noise. This project proposes a GAN-based approach that learns to denoise directly from data through adversarial training.

---

## Motivation

- Classical denoising techniques are limited in handling complex noise models.
- Neural networks can learn robust, non-linear mappings from noisy to clean data.
- A GAN framework offers the advantage of learning both reconstruction and realism.
- The objective is to enable reliable downstream processing by improving point cloud quality.

---

## Methodology

### GAN Architecture

**Generator:**

- Encoder-decoder architecture with residual blocks.
- Multi-head attention mechanism to capture spatial dependencies.
- Outputs clean point clouds from noisy inputs.

**Discriminator:**

- Extracts local geometric features using residual blocks.
- Fully connected layers assess whether the point cloud is real or generated.

### Loss Functions

- **Adversarial Loss:** Encourages the generator to produce realistic outputs.
- **L1 Loss:** Ensures geometric similarity between output and ground truth.

The networks are trained using the Adam optimizer for stability and efficiency.

---

## Results

The model was evaluated under varying levels of Gaussian noise. The performance metrics used include Chamfer Distance and Point-to-Face Distance.

| Noise Level (σ) | Chamfer Distance (×10⁴) | Point-to-Face Distance (×10⁴) |
|------------------|--------------------------|-------------------------------|
| 0.01             | 6.8                      | 5.9                           |
| 0.02             | 7.6                      | 6.8                           |
| 0.03             | 8.3                      | 7.7                           |

- The model maintained stable reconstruction quality even when noise levels were tripled.
- Performance remained competitive compared to other learning-based methods.
- Strong correlation between both evaluation metrics indicates consistent geometric preservation.

---

## Future Work

- Fine-tune the architecture (layer depth, width) to improve detail reconstruction.
- Introduce diffusion steps for better robustness against structured noise.
- Generalize the framework to other domains such as medical imaging and aerial mapping.

---

## Project Structure

