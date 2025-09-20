# Automatic License Plate Recognition (ALPR) 🚗

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5%2B-green.svg)
![EasyOCR](https://img.shields.io/badge/EasyOCR-1.4%2B-red.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

This project is a Python-based application that automatically detects and reads license plates from an image using computer vision techniques with OpenCV and Optical Character Recognition with EasyOCR.

---

## 📖 Table of Contents
- [About the Project](#about-the-project)
- [Technical Workflow](#technical-workflow)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contact](#contact)

---

## 🎯 About the Project

Automatic License Plate Recognition is a technology that uses computer vision to identify vehicle license plates from images or videos. This has numerous real-world applications, including electronic toll collection, traffic monitoring, and automated parking access control.

This project implements a complete ALPR pipeline from raw image to recognized text.

---

## 🛠️ Technical Workflow

The project follows a multi-step computer vision pipeline to achieve its goal:

1.  **Image Preprocessing:** The input image is first converted to grayscale. A **Bilateral Filter** is then applied to reduce noise while preserving edges, which is crucial for the next step.

2.  **Edge Detection:** The **Canny Edge Detection** algorithm is used to find sharp edges in the preprocessed image.

3.  **License Plate Localization:**
    - **Contour Detection:** `cv2.findContours` is used to identify all closed shapes in the edged image.
    - **Shape Analysis:** The contours are sorted by area, and `cv2.approxPolyDP` is used to find the first contour that is a quadrilateral (four-sided polygon), which is assumed to be the license plate.

4.  **Masking and Cropping:** An image mask is created from the located plate contour. This mask is used with a bitwise AND operation to isolate the license plate from the rest of the image, which is then cropped.

5.  **Optical Character Recognition (OCR):** The powerful `EasyOCR` library reads the alphanumeric characters from the clean, cropped plate image.

6.  **Result Visualization:** The recognized text and a bounding box are rendered back onto the original input image to display the final result clearly.

---

## 🏁 Getting Started

Follow these instructions to get the project running on your local machine.

### Prerequisites

This project requires Python and the following libraries. EasyOCR also requires the PyTorch deep learning framework.

- Python 3.8+
- OpenCV
- Matplotlib
- NumPy
- Imutils
- EasyOCR (& PyTorch)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/](https://github.com/)[your-username]/[your-repo-name].git
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd [your-repo-name]
    ```
3.  **Install the required packages:**
    ```bash
    pip install opencv-python matplotlib numpy imutils easyocr
    ```

---

## 🚀 Usage

1.  Place the image you want to analyze in the root directory of the project (e.g., `image4.jpg`).
2.  Update the image file name in the Python script:
    ```python
    img = cv2.imread('your_image_name.jpg')
    ```
3.  Run the script from your terminal:
    ```bash
    python your_script_name.py
    ```
The script will process the image and display the final result with the detected license plate text and bounding box.

---

## 🏆 Results

The model successfully detects the license plate, crops it, and reads the text.

