---
title: "ML Research Assistant"
layout: single
permalink: /SVCC-Internship/
author_profile: true
---

In May 2025 I joined the [Servier Virtual Cardiac Center](https://spaces.facsci.ualberta.ca/svcc/) to research how few Cardiac MRI slices are required to calculate an accurate right ventricular volume under the supervison of Dr. Kumaradevan Punithakumar and Dr. Michelle Noga. 

The first phase of the project was developing a segmentation model to contour large amounts of right ventricular (RV) MRI data (short and long axis views). The industry standard for medical image segmentation is nnUNet, however, we wanted to experiment with training models which were already pretrained on other RV images. We benchmarked nnUNet, the pretrained model as is, the pretrained model trained only on our local data, and finally our proposed apporach of transfer learning (using the pretrained model as the base, then training further). Our proposed approach performed the best, and we published our findings in an international conference; IEEE BIBE 2025.

[Click to Download the Paper!](
