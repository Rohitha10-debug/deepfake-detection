# Deepfake Detection (ResNet-18 baseline)

This project implements a video-level deepfake detector using **face-crop aggregation** and **Grad-CAM explainability**.

## 🚀 Pipeline
1. Extract frames from video
2. Detect and crop faces (MTCNN)
3. Classify each face with ResNet-18 (pretrained on ImageNet, fine-tuned)
4. Aggregate frame-level probabilities into video-level decision
5. Visualize decision regions using Grad-CAM

## 📊 Results
- Validation accuracy: ~97%
- Video-level classification works on test clips (music videos = real, Obama/Marvel deepfakes = fake)
- Misclassifications reduced after data augmentation + balanced loss

## 🔍 Explainability
Grad-CAM overlays show the model focuses on **eye/mouth regions** where deepfake artifacts appear.

## 🧑‍💻 Demo
Run the **demo_notebook.ipynb** in Colab. It loads the trained model and launches a Gradio UI to upload MP4 videos and get predictions.

## 📂 Structure
```
deepfake-detection/
 ├── README.md
 ├── requirements.txt
 ├── demo_notebook.ipynb
 ├── models/
 │    └── best_resnet18_aug_balanced.pth  # trained weights (save in Drive)
 ├── outputs/
 │    ├── video_predictions_demo.csv
 │    └── gradcam_montages/
```
## 📥 Download Pretrained Model

The trained ResNet-18 model weights are hosted on Google Drive. To download:

```bash
pip install gdown
mkdir -p models
gdown --id 1EJhCqkidKCELQZN_zuIkQCMEaiWylq_3 -O models/best_resnet18_aug_balanced.pth


