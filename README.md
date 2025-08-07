# Facial Landmark & Drowsiness Detection

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-orange.svg)](https://opencv.org/)
[![Dlib](https://img.shields.io/badge/Dlib-Face%20Landmark%20Detection-green.svg)](http://dlib.net/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Author](https://img.shields.io/badge/Author-Raafat%20Nagy-blue.svg)](https://github.com/Raafat-Nagy)

---

## Overview

This is a real-time computer vision system that combines face detection, 68-point facial landmark detection, and drowsiness detection using the Eye Aspect Ratio (EAR) method.

Built using OpenCV and dlib, this project is applicable in areas such as:

- Driver alertness and fatigue monitoring systems  
- Human-computer interaction (HCI)  
- Workplace safety and surveillance  
- Augmented reality and emotion analysis  

The system detects a human face from a video stream, identifies key facial landmarks, calculates the eye aspect ratio, and determines if the person is drowsy based on eye closure duration.

**All steps are explained in detail within the Jupyter notebooks to make the project easy to understand and follow.**

---

## Project Structure

```

Facial-Landmark-and-Drowsiness-Detection/
├── 1.Face\_Detection/
│   └── Face\_Detection\_Dlib.ipynb
│
├── 2.Face\_Landmark\_Detection/
│   ├── 1.Face\_Landmark\_Detection\_Dlib.ipynb
│   ├── 2.Face\_Landmark\_Detection\_Dlib\_Class.ipynb
│   └── face\_landmark\_detector.py
│
├── 3.Drowsiness\_Detection/
│   ├── Drowsiness\_Detection\_with\_EAR.ipynb
│   ├── drowsiness\_detection.py
│   └── face\_landmark\_detector.py
│
├── images/
│   └── faces.jpg
│
├── models/
│   ├── mmod\_human\_face\_detector.dat
│   └── shape\_predictor\_68\_face\_landmarks.dat
│
├── requirements.txt
└── README.md

````

---

## Features

### Face Detection

- Two methods:
  - HOG + SVM (fast, suitable for real-time)
  - CNN-based detection using `mmod_human_face_detector.dat` for higher accuracy

### Facial Landmark Detection

- Detects 68 facial landmarks (eyes, nose, jawline, mouth, etc.)
- Implemented in:
  - Notebooks for educational purposes
  - Reusable Python class (`face_landmark_detector.py`)

### Drowsiness Detection

- Calculates Eye Aspect Ratio (EAR)
- Detects when eyes are closed for a number of consecutive frames
- Triggers a visual alert when drowsiness is detected
- Works in real-time using your webcam

---

## Installation

Make sure Python 3.6 or higher is installed.

Install dependencies using:

```bash
pip install -r requirements.txt
````

Note: On some systems (especially Windows), you may need to install CMake or Visual Studio Build Tools to compile dlib.

---

## Download Pre-trained Models

| Model                                   | Description                 | Download                                                                    |
| --------------------------------------- | --------------------------- | --------------------------------------------------------------------------- |
| `mmod_human_face_detector.dat`          | CNN-based face detector     | [Download](https://dlib.net/files/mmod_human_face_detector.dat.bz2)          |
| `shape_predictor_68_face_landmarks.dat` | 68-point landmark predictor | [Download](https://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2) |

After downloading and extracting, place the `.dat` files into the `models/` directory.

If links do not work, visit the [official dlib models page](http://dlib.net/).

---

## How to Run

### 1. Launch Jupyter Notebooks

Navigate to the folder and open one of the following:

* `Face_Detection_Dlib.ipynb`
* `1.Face_Landmark_Detection_Dlib.ipynb`
* `2.Face_Landmark_Detection_Dlib_Class.ipynb`
* `Drowsiness_Detection_with_EAR.ipynb`

### 2. Run Python Scripts

#### Facial Landmark Detection:

```bash
cd 2.Face_Landmark_Detection/
python face_landmark_detector.py
```

#### Drowsiness Detection:

```bash
cd 3.Drowsiness_Detection/
python drowsiness_detection.py
```

Make sure your webcam is connected and your face is clearly visible in the frame.

---

## What is Eye Aspect Ratio (EAR)?

The Eye Aspect Ratio is a simple formula that measures eye openness using distances between six eye landmarks:

```
EAR = (||p2 − p6|| + ||p3 − p5||) / (2 × ||p1 − p4||)
```

If EAR falls below a certain threshold (e.g., 0.25) for several consecutive frames, the person is considered drowsy.

* Left Eye Landmarks: points 36:41
* Right Eye Landmarks: points 42:47

---