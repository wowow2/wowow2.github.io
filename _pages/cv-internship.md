---
title: "Computer Vision Engineer Intern"
layout: single
permalink: /Chromacare-Internship/
author_profile: true
---

I work as a Computer Vision Engineer Intern at [ChromacareLabs](https://chromacarelabs.com/). They design at home medical testing kits, which can then be analyzed via taking a picture through the Chromacare App. A responsibility of mine is developing a Machine Learning model to segment the test cassette, as well as the test window. This is a part of the larger problem I have solve, which is designing an image processing pipeline which automatically captures an image from a video feed, then reads the test result from the test window. The algorithm has to handle different smartphones having different cameras, thus a calibration step is needed.

I used OpenCV to generate and correct psuedolabels of images of the cassette I collected, then trained a YOLO-obb model to segment the needed parts. We are also working on implementing logic to check auto-capture conditions, remove ambient lighting, and correct illumination non-uniformity among other steps to standardize images across different devices. 

The YOLO-obb segmentation model, as well as the general image processing algorithm will be shipped as part of the Chromacare iOS/Android app; the development and deployment of which I am super excited to play a part in!


