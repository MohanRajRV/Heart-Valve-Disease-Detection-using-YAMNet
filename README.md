# ❤️ Heart Valve Disease Detection using YAMNet

## Heart Valve Disease Classification from Phonocardiogram (PCG) Signals using Transfer Learning

![Python](https://img.shields.io/badge/Python-3.10-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Deep Learning](https://img.shields.io/badge/Deep-Learning-red)
![YAMNet](https://img.shields.io/badge/YAMNet-Transfer%20Learning-green)

---

## 📌 Overview

Heart Valve Disease (HVD) is a major cardiovascular disorder where early diagnosis plays an important role in effective treatment.

Traditional diagnostic techniques such as **Echocardiography, MRI, and CT scans** provide accurate results but require expensive equipment and specialized medical facilities.

This project presents an automated **Heart Valve Disease Classification System** using **Phonocardiogram (PCG) heart sound signals** and **Deep Learning-based Transfer Learning**.

The proposed approach uses Google's pretrained **YAMNet model** to extract high-level audio features from heart sound representations and classify different valve diseases.

The PCG signals are converted into multiple time-frequency representations:

- Linear Spectrogram
- Log-Mel Spectrogram
- Scalogram

These representations are used as input to a modified YAMNet architecture for disease classification.

---

# ✨ Features

- Automated heart valve disease detection from PCG signals
- Transfer learning using pretrained YAMNet
- Multi-class and binary classification
- Comparison of multiple signal representations
- Noise-resistant heart sound analysis
- Lightweight deep learning architecture
- Evaluation on two benchmark datasets

---

# 🫀 Disease Classes

The model supports classification of:

| Class | Disease |
|------|---------|
| Normal | Normal Heart Sound |
| AS | Aortic Stenosis |
| MR | Mitral Regurgitation |
| MS | Mitral Stenosis |
| MVP | Mitral Valve Prolapse |

---

# 📂 Dataset

## 1. Yaseen Heart Sound Dataset

### Purpose:
Multi-class heart valve disease classification

### Classes:

- Normal
- Aortic Stenosis (AS)
- Mitral Regurgitation (MR)
- Mitral Stenosis (MS)
- Mitral Valve Prolapse (MVP)

---

## 2. PhysioNet Challenge 2016 Dataset

### Purpose:
Binary classification and robustness evaluation

### Classes:

- Normal
- Abnormal

The dataset contains real-world noisy PCG recordings collected from different clinical environments.

---

# ⚙️ Methodology

```
PCG Heart Sound Signal
          |
          ↓
Signal Preprocessing
          |
          ↓
Band-pass Filtering
          |
          ↓
Normalization
          |
          ↓
Time-Frequency Representation
          |
 ┌────────┼─────────┐
 ↓        ↓         ↓
Spectrogram  Log-Mel  Scalogram
          |
          ↓
Fragment Generation
          |
          ↓
Modified YAMNet Model
          |
          ↓
Disease Classification
```

---

# 🔬 Data Preprocessing

## 1. Resampling

All recordings are converted into a common sampling frequency:

```
Sampling Rate = 2000 Hz
```

---

## 2. Band-pass Filtering

Noise removal is performed using band-pass filtering:

```
Frequency Range = 25Hz - 600Hz
```

---

## 3. Normalization

Z-score normalization is applied:

```
Normalized Signal = (x - mean) / standard deviation
```

---

## 4. Fragment Generation

The continuous heart sound signals are divided into overlapping segments.

Configuration:

```
Fragment Duration = 1.5 seconds
Input Size = 96 × 64
```

---

# 📊 Feature Extraction

Three different time-frequency representations are evaluated.

---

## 1. Linear Spectrogram

Generated using Short-Time Fourier Transform (STFT).

Advantages:

- Captures time-frequency information
- Provides the highest classification performance

---

## 2. Log-Mel Spectrogram

Represents frequency information using Mel-scale transformation.

Advantages:

- Better representation of human auditory perception
- Commonly used in audio classification tasks

---

## 3. Scalogram

Generated using Continuous Wavelet Transform (CWT).

Advantages:

- Captures localized frequency variations
- Useful for non-stationary heart signals

---

# 🧠 Model Architecture

## Original YAMNet

```
Audio Input
      |
      ↓
Feature Extraction
      |
      ↓
521 Audio Classes
```

---

## Modified YAMNet

```
PCG Spectrogram Input
          |
          ↓
Pretrained YAMNet Feature Extractor
          |
          ↓
Custom Classification Layer
          |
          ↓
Heart Valve Disease Classes
```

---

## Model Modifications

The original YAMNet architecture was modified by:

- Removing the AudioSet classification head
- Adding custom Dense classification layers
- Fine-tuning pretrained features
- Adapting the network for medical audio classification

---

# 🛠 Technologies Used

## Programming Language

- Python 3.10

## Deep Learning

- TensorFlow
- Keras

## Signal Processing

- Librosa
- SciPy
- PyWavelets

## Data Processing

- NumPy
- Pandas

## Visualization

- Matplotlib

---

# 📁 Project Structure

```
Heart-Valve-Disease-YAMNet/
│
├── dataset/
│   ├── yaseen/
│   └── physionet/
│
├── preprocessing/
│   ├── filtering.py
│   ├── normalization.py
│   └── feature_extraction.py
│
├── models/
│   └── yamnet_model.py
│
├── notebooks/
│   └── experiments.ipynb
│
├── train.py
├── evaluate.py
├── requirements.txt
│
└── README.md
```
---

# ▶️ Training

Run training:

```bash
python train.py
```

---

# 📈 Evaluation Results

## Yaseen Dataset

| Feature Representation | Accuracy |
|------------------------|----------|
| Linear Spectrogram | 96% |
| Log-Mel Spectrogram | 95% |
| Scalogram | 93% |

---

## PhysioNet Dataset

| Metric | Score |
|--------|-------|
| Accuracy | 91% |
| UAR | 85.25% |

---

# 🏆 Key Findings

- Linear spectrogram representation achieved the best classification performance.
- Transfer learning using YAMNet reduced training complexity.
- The model achieved robust performance on noisy PCG recordings.
- The lightweight architecture enables future deployment in healthcare applications.

---

# 📚 References

- Google YAMNet: Audio Event Classification Model
- PhysioNet/CinC Challenge 2016 Dataset
- Yaseen Heart Sound Dataset

---

