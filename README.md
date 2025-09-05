 🔍 Deepfake Detection (ResNet-18 + Grad-CAM)

This project implements a video-level deepfake detector using:
- 🎥 Frame extraction  
- 🧑‍🎨 Face-cropping (MTCNN)  
- 🧠 ResNet-18 backbone (fine-tuned on face crops)  
- 📊 Frame → video probability aggregation  
- 🔎 Grad-CAM explainability  

 🚀 Pipeline

1. Extract frames from videos  
2. Detect and crop faces using MTCNN 
3. Classify faces with ResNet-18 (ImageNet pretrained, fine-tuned)
4. Aggregate frame-level probabilities → video-level prediction  
5. Visualize decision regions using Grad-CAM 

 ✅ Results

- Validation Accuracy: ~97%  
- Video-level classification works reliably on test clips  
  - Real videos = music videos  
  - Fake videos = Obama / Marvel deepfakes  
- Misclassifications reduced after:  
  - Data augmentation  
  - Balanced loss weighting  

📉 Confusion Matrix (Validation)  
- Fake: Precision 98.2%, Recall 98.2%  
- Real: Precision 98.8%, Recall 98.8%  

 🔎 Explainability (Grad-CAM)

Grad-CAM overlays show the model focuses on eye/mouth regions,  
where deepfake artifacts most often appear.

Example montages are saved in:  

 🎬 Demo

Run the interactive notebook:  
[`demo_notebook.ipynb`](./demo_notebook.ipynb)

It loads the trained model and supports:  
- Uploading MP4 videos  
- Generating predictions (`real` / `fake`)  
- Visualizing Grad-CAM overlays  

 📂 Project Structure
deepfake-detection/
│── README.md
│── requirements.txt
│── demo_notebook.ipynb
│
├── models/
│ └── best_resnet18_aug_balanced.pth # trained weights (download via Drive)
│
├── outputs/
│ ├── video_predictions_demo.csv
│ └── gradcam_montages/

 📥 Download Pretrained Model

The fine-tuned ResNet-18 weights are stored on Google Drive.  
Download using:

```bash
pip install gdown
mkdir -p models
gdown --id 1EJhCqkidKCELQZN_zuIkQCMEaiWylq_3 -O models/best_resnet18_aug_balanced.pth

git clone https://github.com/Rohitha10-debug/deepfake-detection.git
cd deepfake-detection
pip install -r requirements.txt

outputs/video_predictions_demo.csv

