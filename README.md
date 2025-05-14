# 🧠 Advanced Driver Detection System using YOLOv5

This repository implements a **two-stage driver detection pipeline** using YOLOv5, custom logic for cropping the driver’s region, and final bounding box adjustment. The model is optimized for real-world driving scenarios to identify the **driver only** from traffic images or video streams.

---

## 🔍 Project Summary

This system performs:

1. **Vehicle Detection** – Detects all cars in the frame using YOLOv5.
2. **Driver Side Cropping** – Automatically extracts only the driver's side from the detected car (e.g., 40% from the right side).
3. **Driver Detection** – Applies another YOLOv5 model to detect the driver inside the cropped region.
4. **Bounding Box Alignment** – Maps the detected driver back to the original image coordinates.

---

## 🎯 Visual Overview

```
Full Image ➝ YOLO Car Detection ➝ Driver Side Crop ➝ YOLO Face/Person Detection ➝ Driver Output
```

Example image:

![Pipeline Output](https://github.com/jonibek95/driver-detection/assets/.../output.jpg)

---

## 💡 Key Features

- 🔍 Two-stage detection pipeline
- 🧠 Custom logic to crop only the **driver side**
- 🎯 Final output shows **driver only**, excludes passengers or pedestrians
- 🛠 Works on both **images** and **videos**
- ⚡ Fast inference using GPU (CUDA) support

---

## 🗂️ File Structure

```
driver-detection/
├── data/                  # Sample images or video
├── face_detector/         # Submodule or fine-tuned YOLO for driver face
├── models/                # YOLO model weights
├── utils/                 # Helper functions
├── demo.py                # Entry-point to run detection
├── requirements.txt       # Dependencies
└── README.md
```

---

## ⚙️ Installation

```bash
git clone https://github.com/jonibek95/driver-detection.git
cd driver-detection
pip install -r requirements.txt
```

Ensure you have:
- Python 3.8+
- PyTorch
- OpenCV
- YOLOv5 dependencies

---

## ▶️ How to Run

### On a single image:

```bash
python demo.py --source path/to/image.jpg
```

### On a video:

```bash
python demo.py --source path/to/video.mp4
```

### Inside code (example):

```python
weights_path = 'yolov5x6.pt'
image = 'car_person.jpg'
detector = Detector(weights_path)
detector.Prediction_1(image)
detector.Prediction_2()
```

---

## 📌 Core Classes and Logic

- `Prediction_1()`: Runs car detection and crops the driver side.
- `Prediction_2()`: Runs person detection inside the crop and adjusts coordinates.
- `mainA(video_path)`: Full pipeline for processing video.

---

## 📦 Output

- `crop.jpg`: Cropped driver region
- `output.jpg`: Final detection with bounding box
- `driver_video.avi`: Video with driver detections drawn

---

## 📜 License

MIT License

---

## 👤 Author

**Jonibek Raupov**  
GitHub: [@jonibek95](https://github.com/jonibek95)
