# 🎨 ChromaRevive: AI Video & Image Colorizer

**ChromaRevive** is a deep learning-based tool designed to restore color to black-and-white historical footage and photography. Built on PyTorch and ResNet18, it utilizes Transfer Learning to achieve vibrant results with minimal training data.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-red)
![Status](https://img.shields.io/badge/Status-Active-success)
![AI Generated](https://img.shields.io/badge/Made%20with-AI%20Assistance-purple)

## ✨ Features

*   **Dual-Mode Processing:** Colorizes both single Images (`.jpg`, `.png`) and Videos (`.mp4`).
*   **ResNet-18 U-Net Architecture:** Uses a pre-trained backbone for high-level feature recognition.
*   **Temporal Smoothing:** Video processing includes a frame buffer to prevent "flickering" colors between frames.
*   **High-Quality Inference:**
    *   **Test-Time Augmentation (TTA):** Dual-pass prediction (Normal + Flipped) for stability.
    *   **Lanczos Upscaling:** High-quality resizing to preserve sharpness.
    *   **Bilateral Filtering:** Heavy edge-preserving smoothing for a "painted" look.
*   **Smart Training:** Includes Color-Weighted Loss and Dynamic Learning Rate Scheduling.

## 🤖 AI Development Disclaimer

> **Transparency Note:** This project was conceptualized, architected, and coded with the assistance of Large Language Models (AI). While the logic utilizes standard Deep Learning practices (Autoencoders, Lab Color Space), the specific implementation and optimization of these scripts were generated through human-AI collaboration.

## 🛠️ Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/ChromaRevive.git
    cd ChromaRevive
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Check for GPU (Optional):**
    This tool runs on CPU, but an NVIDIA GPU (CUDA) is highly recommended for speed.

## 🚀 Usage

### Step 1: Train the Model
You need to teach the AI what colors look like first.

1.  Create a folder named `train_images` inside the project directory.
2.  Add **50-100 colorful images** (JPG/PNG) to that folder. (Nature, portraits, and cityscapes work best).
3.  Run the trainer:
    ```bash
    python train.py
    ```
4.  Follow the prompt to select GPU or CPU.
5.  Once finished, it will save `fast_color_model.pth`.

### Step 2: Colorize!
1.  Have your black-and-white file ready (e.g., `video.mp4` or `photo.jpg`).
2.  Run the main script:
    ```bash
    python main.py
    ```
3.  Select whether you are processing an Image or Video.
4.  Drag and drop your file into the terminal window.
5.  Wait for the magic to happen! The result will be saved with `_ultimate` appended to the filename.

## ⚙️ Configuration

You can open `main.py` and adjust the **Extreme Quality Settings** at the top of the file:

```python
SATURATION_BOOST = 1.4       # Increase for more vibrant colors
USE_TTA = True               # Double-pass prediction (Slower, better quality)
USE_HEAVY_FILTERING = True   # Enable edge-preserving smoothing (Slowest)
