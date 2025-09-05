---
title: Deepfake Detection
author: Rohitha
---

# 🎯 Project Goal
- Detect deepfake videos using face crops + ResNet18
- Explain predictions with Grad-CAM

---

# 🔑 Pipeline
Video → Frames → Face Detection → ResNet18 → Aggregation → Prediction

- Input: short MP4
- Output: real vs fake probability
- Threshold = 0.7 for fake

---

# 📊 Results & Explainability
- Validation Accuracy: **97%**
- Video-level classification correct on test set
- Grad-CAM focuses on **face artifacts** (eyes, mouth)

![GradCAM Example](outputs/gradcam_montages/sample.jpg)

