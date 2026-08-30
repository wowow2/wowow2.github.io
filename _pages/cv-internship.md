---
title: Machine Learning Developer
layout: experience
permalink: /Chromacare-Internship/
---

I work as a Machine Learning Developer at [ChromacareLabs](https://chromacarelabs.com/), building computer vision features for a consumer healthcare app that analyzes at-home medical test kits.

I architected a cloud-based deep learning regression pipeline engineered to extract and quantify 1D signal intensity profiles from diagnostic tests, spanning CV-based feature extraction through deep neural network architecture design, training, and evaluation for production deployment on AWS. The primary focus is ensuring highly consistent biomarker concentration predictions, mitigating test-to-test variance across physical cassettes of the same concentration via custom model architectures and calibration logic that stabilize predictions against artifacts, noise, and varying illumination.

To support this, I manage large-scale datasets (HDF5, PostgreSQL on RDS, S3) via a relational schema for training data and metadata; I built API endpoints and visualization tooling for data collection and model testing, tracking prediction consistency and data quality to continuously refine training datasets. I also collaborated with mobile engineers to implement on-device capture quality checks for the iOS and Android apps, guaranteeing that only high-fidelity images are transmitted to the server for analysis.

A core part of my role is working directly with chemists to co-develop the test itself. I provide data-driven feedback on assay chemistry and lot-to-lot variation — analyzing signal stability and failure modes to inform iterations on formulation and cassette design — tightening the loop between wet-lab and software.

I also helped build the software team. I referred colleagues who were subsequently hired, and together we have established engineering practices for a small, cross-functional group that bridges chemistry, ML, and product. Our work is currently supporting FDA and Health Canada submissions, including documentation, validation, and reproducibility for the analytical and software components.
