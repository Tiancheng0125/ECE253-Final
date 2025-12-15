# ECE253 Final Project: A Unified Comparative Framework for Image Restoration

## 1. Dehazing (Direction A)
1.  Navigate to the directory: `Dehazing/notebooks/`.
2.  Open and run the following notebooks to reproduce the results found in the report:
    * **DCP Experiments:** Run `dcp_outdoor.ipynb` (for RESIDE outdoor photos), `dcp_indoor.ipynb` (for RESIDE indoor photos) and `dcp_ohaze.ipynb` (for O-HAZE).
    * **AOD-Net Experiments:** Run `aod.ipynb` (for RESIDE) and `aod_ohaze.ipynb` (for O-HAZE).
    * **Our own photos:** Run `myhaze.ipynb`.
3.  The notebooks will generate visual comparisons and print quantitative metrics (PSNR, SSIM, NIQE, etc.).

---

## 2. Deblurring (Direction B)

### How to Run
1.  Open MATLAB.
2.  Navigate to the `Deblurring/` directory.
3.  Run the script `run.m`.
4.  This script will execute the blind deblurring algorithms and display the test results.

---

## 3. Denoising (Direction C)

# Comparative Image Denoising: Wavelet, SVR, and DnCNN

This repository contains the source code and experimental framework for a comparative study of image denoising methodologies. The project evaluates classical signal processing (**Wavelet Transform**), machine learning techniques (**Support Vector Regression - SVR**), and deep residual learning (**DnCNN**) across various noise levels.

## 📂 Project Structure

```text
├── data/                    # Dataset directory
│   ├── clean/               # Ground truth / Reference images
│   ├── noisy/               # Noisy input images (synthetic)
│   └── real/                # Real-world noisy images (no ground truth)
│
├── Results/                 # Output directory for plots, CSV logs, and processed images
│
├── Project_Folder/          # Utility scripts and helper functions
│
├── Denoising.ipynb          # [MAIN] Comprehensive benchmark (Wavelet vs SVR vs DnCNN)
├── Denoising2.ipynb         # Extended experiments and alternative metrics
├── figurePSNR.ipynb         # Generates PSNR/SSIM comparison plots for the report
│
├── dncnn.ipynb              # DnCNN training and validation pipeline
├── dncnn2.ipynb             # Alternative DnCNN experiments
├── dncnn_bicycle.ipynb      # DnCNN demo specifically on the 'bicycle' image
│
├── denoising_svr.ipynb      # SVR implementation pipeline
├── bicycle_svr.ipynb        # SVR demo specifically on the 'bicycle' image
├── SVR_PLUS.ipynb           # SVR hyperparameter tuning and variants
│
├── bicycle.ipynb            # General baseline visualization for 'bicycle' image
├── wavelet_bicycle*.ipynb   # Wavelet denoising demos
│
└── requirements.txt         # Python dependencies

Environment Setup
Option A: Local Installation (Recommended)
It is recommended to use a virtual environment with Python 3.9+.

1. Create and activate a virtual environment:

Bash

# Create virtual environment
python -m venv venv

# Activate environment
# macOS/Linux:
source venv/bin/activate
# Windows:
# venv\Scripts\activate
2. Install Core Dependencies:

Bash

pip install -U pip
pip install numpy opencv-python matplotlib scikit-learn scipy pillow scikit-image
3. Install PyTorch:

For NVIDIA GPU (CUDA 12.1):

Bash

pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu121](https://download.pytorch.org/whl/cu121)
For CPU only:

Bash

pip install torch torchvision torchaudio
Option B: Google Colab
Upload the entire project folder to your Google Drive.

Mount Google Drive in the notebook using:

Python

from google.colab import drive
drive.mount('/content/drive')
Navigate to the project folder and run the notebooks.

📊 Data Preparation
To reproduce the results, organize your image datasets in the data/ directory:

Paired Evaluation: Place clean reference images in data/clean/. The notebooks will automatically add Gaussian noise during execution or look for pre-generated noisy images in data/noisy/.

Real-world Tests: Place real noisy images (e.g., from SIDD or captured photos) in data/real/.

> Note: Verify the file paths in the "Config" or "Path" cell at the top of Denoising.ipynb if your data location differs.

🚀 Usage Guide
1. Run the Full Benchmark
To evaluate all three methods (Wavelet, SVR, DnCNN) and calculate PSNR/SSIM metrics:

Open Denoising.ipynb.

Run all cells.

Results will be logged, and comparative images will be saved to the Results/ folder.

2. Method-Specific Experiments
If you want to focus on a single method or run single-image demos:

Deep Learning: Run dncnn.ipynb (General pipeline) or dncnn_bicycle.ipynb (Single image demo).

Machine Learning: Run denoising_svr.ipynb or bicycle_svr.ipynb.

Classical: Run wavelet_bicycle*.ipynb.

3. Generate Report Figures
To create the summary plots (e.g., PSNR vs. Noise Level) used in the report:

Ensure you have run the benchmark notebooks first to generate result logs.

Open figurePSNR.ipynb.

Run the notebook to generate and save high-resolution plots to Results/.

📈 Metrics
The framework evaluates performance using the following metrics:

PSNR (Peak Signal-to-Noise Ratio): Measures pixel-wise reconstruction fidelity against ground truth.

SSIM (Structural Similarity Index): Measures perceptual structural preservation.

NIQE / BRISQUE: (Optional) Non-reference metrics for real-world images where ground truth is unavailable.

📝 Notes on Reproducibility
Random Seeds: All experiments use fixed random seeds (set at the start of notebooks) to ensure deterministic noise generation and model initialization.

Hardware: A GPU is highly recommended for running DnCNN training and inference, though CPU execution is supported.

Model Weights: If using pre-trained DnCNN models, ensure the checkpoint paths in the notebook match your local file structure.

---

## Release Note
This code corresponds to the submission version **v1.0-report-version**.
