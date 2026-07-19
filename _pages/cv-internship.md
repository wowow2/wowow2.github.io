---
title: Computer Vision Engineer Intern
layout: experience
permalink: /Chromacare-Internship/
---

I work as a Machine Learning Developer at [ChromacareLabs](https://chromacarelabs.com/), building computer vision features for a consumer healthcare app that analyzes at-home medical test kits. 

I designed and deployed a deep learning regression pipeline engineered to extract and quantify 1D signal intensity profiles from diagnostic tests. The primary focus of my work was ensuring highly consistent biomarker concentration predictions, mitigating test-to-test variance across physical cassettes of the same concentration. To achieve this, I developed custom model architectures and calibration logic that stabilize predictions against physical artifacts, noise, and varying illumination.

To support this regression task, I engineered a robust data infrastructure (HDF5, PostgreSQL, AWS S3) for large-scale dataset management. I built internal visualization tooling to track prediction consistency and data quality, and generated refined training datasets to continuously improve model accuracy. I also collaborated with mobile engineers to deploy these models to iOS and Android, implementing the necessary capture quality checks and post-processing logic to guarantee only high-fidelity signals proceed to analysis.
