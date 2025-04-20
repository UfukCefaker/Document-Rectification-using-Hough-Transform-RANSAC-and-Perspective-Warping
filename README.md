# Document Dewarping with Classical Computer Vision Techniques

This repository contains the implementation of a complete document dewarping pipeline using only **NumPy** and fundamental image processing operations. The project was developed as part of the **BBM 418 - Computer Vision Laboratory** course at Hacettepe University.

## 🧠 Overview

The pipeline was designed to correct geometric distortions in document images by detecting edges, estimating perspective, and performing homographic transformations. It supports six different distortion classes:
- Curved
- Fold
- Incomplete
- Perspective
- Random
- Rotate

## 🔧 Methods

For each input image, the following steps are applied:

1. **Edge Detection:** Canny edge detection to identify document boundaries.
2. **Hough Transform:** Custom Hough Line Transform to detect lines in the edge map.
3. **RANSAC Line Refinement:** Removes outliers and keeps dominant lines.
4. **Quadrilateral Detection:** Groups line intersections to estimate document corners.
5. **Perspective Warping:** Applies a custom homography matrix to warp the document.
6. **SSIM Evaluation:** Compares the warped image with the ground truth using Structural Similarity Index (SSIM).

## 📊 Results

- The pipeline was tested on the first 50 images from each class.
- The top 2 images with the highest SSIM score per class were selected.
- The number of quadrilateral detection failures was recorded.

### 📈 Average SSIM per Class

| Class       | SSIM  |
|-------------|-------|
| Curved      | 0.245 |
| Fold        | 0.226 |
| Incomplete  | 0.202 |
| Perspective | 0.260 |
| Random      | 0.162 |
| Rotate      | 0.246 |

### ✅ Quadrilateral Detection Success

| Class       | Successful Detections (out of 50) |
|-------------|-----------------------------------|
| Curved      | 38                                |
| Fold        | 44                                |
| Incomplete  | 42                                |
| Perspective | 41                                |
| Random      | 45                                |
| Rotate      | 46                                |

## 🧩 Observations

- Perspective and curved distortions gave the best visual and SSIM results.
- The rotate class had the highest consistency due to axis-aligned shapes.
- Detection sensitivity was highly influenced by the Hough threshold.
- Failures were mostly caused by edge occlusions and background textures.

## 📁 Folder Structure

