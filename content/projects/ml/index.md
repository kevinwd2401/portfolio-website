---
title: "Image2GPS"

tags:
  - Python
  - PyTorch
  - ResNet
---

![](/images/projects/image2gps.png)


For our final project for CIS 5190, our team of 3 built a computer vision regression pipeline to predict GPS coordinates from campus images. Model performance was validated using Haversine distance to measure physical GPS prediction error. We started by collecting and preprocessing a custom dataset of 1,667 GPS-labeled images, converted it into a Hugging Face Dataset, and trained ResNet-based latitude/longitude regression models.

We used: normalized coordinate targets, Smooth L1 loss, AdamW, learning-rate scheduling, weight decay, and gradient clipping.

We were able to achieve 47.53m average prediction error and 9.19ms average inference time, outperforming the class average in both accuracy and speed.