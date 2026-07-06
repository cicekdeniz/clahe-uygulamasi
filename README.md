# Underwater Image Enhancement and Object Detection (CLAHE + YOLOv5)

This project investigates how underwater image enhancement affects object detection performance. As part of an internship, YOLOv5 models trained on raw underwater images were compared against models trained on enhanced images.

## Project Goal

Underwater images are challenging for object detection due to color distortion, low contrast, and blurriness. This project aims to answer:

> Do image enhancement steps (red channel compensation + CLAHE + sharpening) actually improve a YOLOv5 model's detection performance?

## Pipeline

1. **Red Channel Compensation** — Corrects the color imbalance caused by the rapid absorption of red wavelengths underwater.
2. **CLAHE (Contrast Limited Adaptive Histogram Equalization)** — Enhances local contrast in the image.
3. **Sharpening** — Highlights edges and fine details.

Pipeline effectiveness was evaluated using:

- **Quality metrics:** UIQM, UCIQE
- **Utility metrics:** Entropy, Edge Score, Detection Score

## Dataset and Model Training

- A small-scale, YOLO-formatted, labeled underwater image dataset was used.
- The dataset was used to train the model in two separate setups:
  - Training on **raw images**
  - Training on **CLAHE-enhanced images**
- Separate `data.yaml` configurations were created for each setup, and training was run on YOLOv5.

## Results

The model trained on CLAHE-enhanced images showed a noticeable improvement in **precision, recall, and mAP** compared to the model trained on raw images. Training loss curves, F1/PR curves, and confusion matrices are included in this repository (`results.png`, `F1_curve.png`, `PR_curve.png`, `confusion_matrix.png`).

**Overall conclusion:** Image enhancement steps make it easier for the model to learn and detect objects in underwater conditions.

## Folder Structure

```
.
├── classify/              # Classification-related files
├── data/                  # Dataset configurations
├── models/                # Model architectures
├── segment/                # Segmentation files
├── underwater_dataset/    # Underwater image dataset
├── utils/                 # Helper functions
├── train.py               # Training script
├── val.py                 # Validation script
├── detect.py               # Inference script
├── best.pt / last.pt      # Trained model weights
└── CLAHE_pipeline.docx    # Pipeline documentation
```

## Tech Stack

- Python
- OpenCV (CLAHE, image processing)
- YOLOv5 (Ultralytics)
- PyTorch

## Notes

This project is built on top of the [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5) framework. See the original YOLOv5 license for licensing terms (AGPL-3.0).

---

_Developed as part of an internship at AGH University of Krakow._
