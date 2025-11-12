# Analysis of Diffusion Model's Inference Mechanism Using XAI Techniques
This repository contains the implementation and analysis for understanding the inference mechanism of diffusion models using Explainable AI (XAI). 
**This research was conducted by the only undergraduate team selected for the KCC 2024 Explainable AI Workshop, where Doeun Kim participated as the presenting author.**
The study investigates how Denoising Diffusion Probabilistic Models (DDPM) focus on different pixel regions across timesteps by applying Integrated Gradients, Gradient SHAP, and Occlusion techniques. The goal is to interpret the decision-making process behind diffusion-based image generation.

[📄 Download Poster (PDF)](https://github.com/doeunyy/xai-research-paper/blob/main/xai-poster-eng.pdf)


## Table of Contents

1. [Overview](#overview)
2. [Project Timeline](#project-timeline)
3. [Key Contributions](#key-contributions)
4. [Methodology](#methodology)
5. [Experimental Results](#experimental-results)
6. [Authors](#authors)

## Overview
Diffusion models achieve high-quality image synthesis through iterative denoising, but their internal operations remain difficult to interpret due to their black-box nature. This project applies XAI techniques to reveal how model attention evolves throughout the diffusion process.
Using 100 noisy samples across 100 timesteps for four ImageNet classes (Persian cat, Siamese cat, Egyptian cat, Tiger), we track attribution changes and likelihood progression to analyze how the model identifies and reconstructs essential visual features.

## Project Timeline
A concise summary of the Ewha DoInJi project timeline leading to the development of this research.
- Mar–Apr 2024: Initial literature study on diffusion models, including DDPM, DDIM, LDM, and score-based generative processes.
- May 2024: Secondary paper review on model optimization (quantization, distillation, pruning, token merging).
- Late May 2024: Implemented and validated multiple diffusion models (DDPM, DDIM, Stable Diffusion, LDM) using reproducible Jupyter notebooks.
- May–Jun 2024: Studied XAI techniques and executed hands-on experiments using Captum (Integrated Gradients, Grad-SHAP, Occlusion).
- Jun 2024: Authored and submitted the XAI workshop paper; poster selected for presentation at the KCC 2024 Explainable AI Workshop.

## Key Contributions
- Applied Integrated Gradients, Gradient SHAP, and Occlusion to diffusion model inference.
- Constructed timestep-wise noisy datasets for four ImageNet classes.
- Identified critical intervals where classification likelihood increases sharply.
- Demonstrated shared feature development patterns: outline → key features → fine details.
- Provided cross-class comparative visualizations and analysis.

## Methodology
### Model Configuration
- Base model: DDPM (Denoising Diffusion Probabilistic Models)
- Classifier: Pretrained ResNet-18 (ImageNet-1000)
- Classes analyzed: Persian cat, Siamese cat, Egyptian cat, Tiger
- 100 noisy images sampled per class across timesteps 1–100

### XAI Techniques
- Integrated Gradients: Gradient-based attribution relative to a baseline
- Gradient SHAP: Hybrid technique using multiple baselines for stability
- Occlusion: Perturbation method masking regions to measure significance

### Likelihood Tracking
Softmax outputs of the classifier were analyzed across timesteps to identify critical moments where classification confidence sharply increases.

## Experimental Results
### Attribution Analysis
- Early timesteps: Model relies on overall silhouette and broad structural cues.
- Mid timesteps (cats: around 40–60): Attribution sharply focuses on eyes and facial boundaries.
- Tiger class: Earlier spike (~30–40) due to stripe features, followed by facial refinement.

### Likelihood Insights
- Cat classes consistently reach peak confidence around timestep 60.
- Tiger class shows initial confidence growth near timestep 30 due to distinctive textures.
- Evolution of attention resembles human drawing: coarse shapes → textures → fine details.

## Conclusion
XAI techniques successfully reveal the internal reasoning of diffusion models across timesteps. The findings demonstrate a clear progression of model attention from global structure to class-specific features and finally to detailed facial characteristics. These insights can guide improvements in interpretability, robustness, and text-to-image alignment for diffusion models.

## Authors

- Doeun Kim (Co-first Author) — [doeunkim.cs@gmail.com](mailto:doeunkim.cs@gmail.com)
- Jieun Byeon (Co-first Author)
- Inae Park (Co-first Author)

Department of Computer Science and Engineering <br>
Ewha Womans University
