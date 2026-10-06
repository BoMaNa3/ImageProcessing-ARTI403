# Image Processing Lab 1

Name: Maan Abdullah Alghamdi  
ID: 2240001433  
Course: ARTI 403 - Image Processing

## Overview

In this lab, I load, display, and save grayscale images using OpenCV and Pillow. I represent images as NumPy arrays, inspect their pixel values and dimensions, and apply basic image operations.

## My Files

- `Lab_1_Maan_Alghamdi.ipynb`: my notebook, including saved outputs.
- `Lab_1_Maan_Alghamdi.pdf`: a PDF of my notebook's text, code, and saved outputs. The long embedded TIFF data string is abbreviated in the PDF and preserved in the notebook.

## What I Do

1. I prepare the camera sample from scikit-image and restore the embedded course Lena image.
2. I display both images and load them using OpenCV and Pillow.
3. I save images as JPEG files.
4. I inspect array types, shapes, dimensions, and pixel values.
5. I calculate Lena's minimum, maximum, mean, and standard deviation.
6. I crop Lena with `[50:200, 50:200]`, create a negative, increase brightness by 50 with clipping, flip the image horizontally, and apply a binary threshold of 128.
7. I compare and save my processed results.

## How I Run It

I use Python 3 with Jupyter Notebook or Google Colab. For a local setup, I install:

```bash
python -m pip install notebook numpy matplotlib pillow scikit-image opencv-python
```

I start Jupyter with `jupyter notebook`, open my notebook, and run all cells from top to bottom. The Lena image is embedded, so I do not need to supply it separately.

## My Outputs

I create `Images/` for source images and `lab1_results/` for saved results in my working directory. I save the cropped, negative, brighter, flipped, and binary Lena images, plus a comparison figure.

In the saved outputs, I observe a camera shape of `(512, 512)` and a Lena shape of `(256, 256)`. My cropped image has shape `(150, 150)`. Lena's mean intensity is 124.01 and its standard deviation is 47.84.

