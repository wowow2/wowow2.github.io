---
title: "ML Research Assistant"
layout: single
permalink: /SVCC-Internship/
author_profile: true
---

In May 2025 I joined the [Servier Virtual Cardiac Center](https://spaces.facsci.ualberta.ca/svcc/) to research how few Cardiac MRI slices are required to calculate an accurate right ventricular volume under the supervison of Dr. Kumaradevan Punithakumar and Dr. Michelle Noga. 

The first phase of the project was developing a segmentation model to contour large amounts of right ventricular (RV) MRI data (short and long axis views). The industry standard for medical image segmentation is nnUNet, however, we wanted to experiment with training models which were already pretrained on other RV images. We benchmarked nnUNet, the pretrained model as is, the pretrained model's raw architecture trained only on our local data, and finally our proposed apporach of transfer learning (using the pretrained model as the base, then training further). Our proposed approach performed the best, and we published our findings in an international conference; IEEE BIBE 2025.

Publishing at an international conference as a first author is an acomplishment I am very proud of; I learnt a lot not only about processing/analyzing/visualizing medical images but also about putting my finding into the formal formatting of a research paper and communicating our ideas through intricate visualizations.

[Click to see the paper!](/assets/IEEE_BIBE2025.pdf)

Currently I am working on using the large dataset created by the model to develop algorithms to reduce slices used to compute volume. Our baseline method is integrating over all short axis slices, and our apporaches range from naively reducing every other slice to utilizing long axis slice diameters in a regression model (linear regression and more complex apporaches such as gradient boosting). 
