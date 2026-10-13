# HYPERLUMA: Advanced Eye Disease Detection & Hyperspectral Analysis System

[![Python](https://img.shields.io/badge/Python-3.8%20%7C%203.9%20%7C%203.10%20%7C%203.11-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![GUI](https://img.shields.io/badge/GUI-PyQt5%20%2F%20PyQt6-41CD52?style=for-the-badge&logo=qt&logoColor=white)](https://riverbankcomputing.com/software/pyqt/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20Raspberry%20Pi-0078D6?style=for-the-badge)](https://github.com/)
[![Watch Demo Video](https://img.shields.io/badge/Google%20Drive-Watch%20Demo%20Video-red?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1i_NHpuDHJY7bcHjHUrK5iOLCYtxX1rgb/view?usp=drive_link)

Developed by **SMART** (*Sanjivani Multidisciplinary AI Research & Technology*).

---

## 📌 Overview

**HYPERLUMA** is an end-to-end, medical-grade diagnostic application that combines state-of-the-art Deep Learning computer vision, Explainable Artificial Intelligence (XAI), and Hyperspectral Imaging (HSI) for rapid screening, detection, and spectral signature profiling of ophthalmic pathologies.

Designed for clinical desktop environments as well as low-power edge devices (such as Raspberry Pi 4/5 portable fundus cameras), HYPERLUMA enables clinicians, researchers, and healthcare professionals to perform real-time screenings and generate diagnostic reports.

---

## 👁️ Supported Diagnostic Categories

HYPERLUMA classifies retinal fundus imagery into 6 distinct clinical classes:

| Class | Medical Condition | Description & Biomarkers |
| :--- | :--- | :--- |
| **AMD** | Age-related Macular Degeneration | Macular drusen, pigmentary changes, and subretinal fluid deposits. |
| **Cataract** | Cataract | Crystalline lens opacification and media haze obstructing fundus visibility. |
| **Dementia** | Dementia / Neurodegenerative Markers | Retinal microvascular alterations and nerve fiber layer attenuation linked to cognitive decline. |
| **Diabetes** | Diabetic Retinopathy | Microaneurysms, retinal hemorrhages, hard exudates, and cotton-wool spots. |
| **Glaucoma** | Glaucoma | Optic cup-to-disc ratio (CDR) enlargement and neuroretinal rim thinning. |
| **Normal** | Healthy Fundus | Normal optic disc, healthy vasculature, and clear macular anatomy. |

---

## ✨ Key Features

### 🧠 1. Deep Learning & Ensemble Inference Engine
- **Diverse Backbone Architectures**:
  - **Swin Transformer**: Hierarchical vision transformer utilizing shifted windows for multi-scale feature representation.
  - **EfficientNetV2-S**: Fast and parameter-efficient ConvNet with fused-MBConv layers.
  - **ResNeXt-50**: Multi-branch aggregated residual transformations.
  - **FNet**: 2D Discrete Fourier Transform (DFT) token mixing replacing traditional attention for ultra-fast inference.
  - **Perceiver IO**: Cross-attention architecture for arbitrary modalities and spatial representations.
- **Soft-Voting Ensemble Models**:
  - `effnet_fnet_ensemble.pth`
  - `effnet_perceiver_ensemble.pth`
  - `effnet_swin_ensemble.pth`
  - `resnext_perceiver_ensemble.pth`
  - `swin_fnet_ensemble.pth`

### 🔍 2. Explainable AI (XAI)
- **Grad-CAM Integration**: Visualizes class-activation heatmaps directly over fundus images, highlighting specific regions (optic cup, macula, hemorrhages) guiding the model's prediction.
- Builds transparency for clinical decision support and tele-ophthalmology review.

### 🌈 3. Hyperspectral Analysis & Spectral Disease Mapping
- **HSI Cube Loader**: High-dimensional datacube ingestion (`.mat`, `.npy`, ENVI raw files).
- **Interactive ROI Selector**: Custom polygon and bounding-box region-of-interest extraction.
- **Reflectance Signature Curves**: Continuous wavelength plotters mapping spectral reflectance values to optical absorption signatures for specific retinal conditions.
- **Disease-Specific Band Indicators**: Automated marking of wavelengths that correspond to hemoglobin, melanin, and lipid absorption peaks.

### 📷 4. Real-Time Hardware Capture & Video Feed
- Direct acquisition from USB fundus cameras, industrial webcams, and Raspberry Pi Camera Modules (v2/v3).
- Live quality validation: illumination balance, contrast levels, and blur detection before model inference.

### 📄 5. Clinical Reporting & Patient Records
- Patient metadata tracking (Patient ID, demographic details, timestamp).
- Export diagnostic results into comprehensive PDF medical reports, structured JSON records, and Excel spreadsheets.

### ⚡ 6. Dual-Platform Deployment (Windows & Raspberry Pi)
- **Windows**: Ready-to-run packaged installers (`HYPERLUMA_Setup_v2.0.0.exe`), standalone binary (`HYPERLUMA.exe`), and batch launcher (`Launch_HYPERLUMA.bat`).
- **Raspberry Pi OS**: Optimized for ARM SBCs with CPU thermal throttling prevention, thread clamping (`OMP_NUM_THREADS=2`), and optional 7-inch touchscreen kiosk mode.
- **Single-File Portable Mode**: `hyperluma.py` embeds all UI elements, icons, loaders, and logic in one portable Python file.

---

## 📁 Repository Structure

```
HYPERLUMA/
├── App/                              # Application modules, installers, and source packages
│   ├── Source Code/                  # Modular application codebase
│   │   ├── assets/                   # Logos, icons, and UI stylesheets
│   │   ├── models/                   # Neural network architectures, loaders & predictors
│   │   ├── spectrum/                 # Hyperspectral cube loaders, band managers & plotters
│   │   ├── ui/                       # PyQt main windows, dialogs & themes
│   │   ├── utils/                    # Camera capture, preprocessing & report generation
│   │   ├── main.py                   # Modular application entry point
│   │   └── run_pi.sh                 # Pi runner script
│   ├── .exe/                         # Packaged executable components
│   └── Installer/                    # Inno Setup installation scripts & outputs
├── Documents/                        # Presentations, research documentation & video demos
│   ├── DR.mp4                        # Clinical demo video
│   ├── HYPERLUMA.pptx                # Project presentation slides
│   └── HYPERLUMADOC.docx             # Project specifications & research paper documentation
├── Evaluation/                       # Quantitative benchmarking & offline evaluation
│   ├── inference.py                  # Lightweight inference script
│   └── inference_v2.py               # Comprehensive evaluation suite (Confusion matrix, Top-1/Top-3, XAI)
├── Models/                           # Pre-trained model weights & ensemble checkpoints (*.pth)
├── Output/                           # Diagnostic outputs, generated heatmaps & previews
│   ├── Output_Imgs/                  # Sample screenshots and clinical predictions
│   └── README.md                     # Output directory specifications & video link
├── SRC/                              # Backup / Source tree copy
├── hyperluma.py                      # Single-File Standalone Portable Application (All-in-One)
├── hyperluma_pi.py                   # Single-File Portable Application for Raspberry Pi OS
├── HYPERLUMA.exe                     # Windows Standalone Application Binary
├── HYPERLUMA_Setup_v2.0.0.exe        # Windows Full Installer Package
├── Launch_HYPERLUMA.bat              # One-click Windows batch launcher
├── run.sh                            # Linux / Raspberry Pi bash launcher
├── run_hyperluma_pi.sh               # Raspberry Pi dedicated launcher
├── Setup_Icon.sh                     # Desktop shortcut installer for Raspberry Pi OS
└── README.md                         # Project documentation
```

---

## 🛠️ Installation & Setup

### Option 1: Windows (Installer / Executable)
1. **Quick Installer**: Run `HYPERLUMA_Setup_v2.0.0.exe` and follow the on-screen setup wizard to install HYPERLUMA as a native Windows program.
2. **Direct Executable**: Double-click `HYPERLUMA.exe` to launch the application immediately without installing dependencies.
3. **From Source (Python)**:
   ```cmd
   :: Clone or extract repository
   cd HYPERLUMA

   :: Create and activate a virtual environment
   python -m venv venv
   call venv\Scripts\activate

   :: Install required dependencies
   pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
   pip install PyQt5 opencv-python numpy scipy matplotlib Pillow loguru timm reportlab openpyxl

   :: Launch via batch file or Python
   Launch_HYPERLUMA.bat
   :: OR
   python hyperluma.py
   ```

---

### Option 2: Linux / Raspberry Pi OS (SBC Setup)
1. **System Packages**:
   ```bash
   sudo apt update
   sudo apt install -y python3-pip python3-venv python3-pyqt5 libxcb-xinerama0 libgl1-mesa-glx
   ```

2. **Virtual Environment & Dependencies**:
   ```bash
   cd ~/HYPERLUMA
   python3 -m venv venv
   source venv/bin/activate

   pip install --upgrade pip
   pip install torch torchvision --extra-index-url https://download.pytorch.org/whl/cpu
   pip install opencv-python-headless numpy scipy matplotlib Pillow loguru timm reportlab
   ```

3. **Desktop Shortcut Setup**:
   ```bash
   chmod +x Setup_Icon.sh run.sh run_hyperluma_pi.sh
   ./Setup_Icon.sh
   ```

4. **Launch Application**:
   ```bash
   # Dedicated Raspberry Pi single-file runner
   ./run_hyperluma_pi.sh

   # Or standard runner
   ./run.sh
   ```

> **Note for Touchscreens / 7-inch displays**: To launch HYPERLUMA in borderless kiosk mode on a connected LCD, uncomment `export HYPERLUMA_KIOSK=1` inside `run_hyperluma_pi.sh`.

---

## 🚀 Usage Guide

### 1. Graphical User Interface (GUI) Workflow
1. **Select Input Source**:
   - **Load Image**: Open a single fundus photograph (`.jpg`, `.png`, `.tif`).
   - **Load Video**: Open a recorded fundus examination video (`.mp4`, `.avi`).
   - **Start Camera**: Connect to a live digital ophthalmoscope or webcam stream.
   - **Hyperspectral Mode**: Ingest `.mat` or `.npy` data cube for wavelength band inspection.
2. **Choose Model**:
   - Select between individual backbones (*Swin Transformer, EfficientNetV2-S, ResNeXt-50, FNet, Perceiver*) or high-accuracy *Ensemble Models*.
3. **Execute Diagnosis**:
   - Click **Detect / Predict**. The AI computes classification probabilities across all 6 classes.
   - View top predictions, confidence percentages, and class-activation Grad-CAM overlays.
4. **Generate Report**:
   - Enter patient ID and clinical notes.
   - Click **Save / Export Report** to produce an official PDF diagnostic sheet and save snapshot records in `Output/`.

---

### 2. Command-Line Model Evaluation & Benchmarking
Use `Evaluation/inference_v2.py` for headless batch inference or model evaluation:

```bash
# Run inference on a single image
python Evaluation/inference_v2.py --model Models/efficientnetv2s_scratch_best.pth --image test_eye.png --arch efficientnetv2s

# Run inference with an ensemble model and Grad-CAM visualization
python Evaluation/inference_v2.py --model Models/effnet_swin_ensemble.pth --image test_eye.png --cam --save-cam output_cam.png

# Evaluate entire test dataset with accuracy and confusion matrix
python Evaluation/inference_v2.py --model Models/effnet_swin_ensemble.pth --data-dir path/to/dataset/test/ --eval
```

---

## 📊 Model Weights Directory

Weights are stored in `Models/`:
- `efficientnetv2s_scratch_best.pth` (~40.9 MB)
- `resnext50_scratch_best.pth` (~46.2 MB)
- `swin_scratch_best.pth` (~55.1 MB)
- `fnet_scratch_best.pth` (~8.1 MB)
- `perceiver_scratch_best.pth` (~11.1 MB)
- `effnet_fnet_ensemble.pth` (~49.0 MB)
- `effnet_perceiver_ensemble.pth` (~52.1 MB)
- `effnet_swin_ensemble.pth` (~96.0 MB)
- `resnext_perceiver_ensemble.pth` (~57.3 MB)
- `swin_fnet_ensemble.pth` (~63.2 MB)

---

## 🎥 Output & Demonstration

For visual examples, interface previews, and sample detection outputs:
- Refer to [Output/README.md](file:///c:/Users/Asus/OneDrive/Desktop/HYPERLUMA/Output/README.md).
- Watch the [Demo Video on Google Drive](https://drive.google.com/file/d/1i_NHpuDHJY7bcHjHUrK5iOLCYtxX1rgb/view?usp=drive_link).

---

## 👥 Research & Organization

**SMART** (*Sanjivani Multidisciplinary AI Research & Technology*)  
Focused on advancing clinical AI diagnostics, tele-ophthalmology, and healthcare accessibility.

---

## ⚖️ License & Disclaimer

*Disclaimer: HYPERLUMA is designed as a clinical assistive tool and academic research platform. Automated model predictions should be reviewed by licensed medical professionals before making patient-care decisions.*
