# ARTI 403 — Image Processing Lab 2

This repository contains my Jupyter notebook, `Lab2_Maan_Alghamdi.ipynb`, for **ARTI 403: Image Processing**. In this lab, I explore how digital images are represented and manipulated, focusing on sampling, quantization, arithmetic operations, and set operations.

## My learning outcome

My goal is to explain how digital images are represented in a computer and how common operations affect image quality and pixel values.

## What I covered

- Loading and displaying grayscale images
- Spatial sampling at different downsampling factors
- Quantization using different numbers of gray levels
- Pixel-wise image addition and subtraction
- `uint8` overflow versus saturated arithmetic
- Grayscale set operations:
  - Complement
  - Union
  - Intersection
  - Difference
  - Symmetric difference
- Binary-mask operations using OR, AND, NOT, and XOR
- Handling image paths containing non-English characters on Windows

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab
- NumPy
- OpenCV
- Pillow
- Matplotlib

Install the required packages with:

```bash
pip install notebook numpy opencv-python pillow matplotlib
```

## Input images I used

I used the following files in an `images` folder located one level above the notebook directory:

```text
images/
├── A.png
├── B.png
├── cameraman.tif
└── lena_gray_256.tif
```

My notebook first looks for `../images`. I also included a Windows fallback path and replacement images for some missing files. I used the original files listed above to produce the intended lab results.

## How to run

1. I open `Lab2_Maan_Alghamdi.ipynb` in Jupyter Notebook or JupyterLab.
2. I confirm that the input images are available in the expected folder.
3. I run all cells from top to bottom.

From a terminal, Jupyter Notebook can be started with:

```bash
jupyter notebook Lab2_Maan_Alghamdi.ipynb
```

## Lab structure

### Demo steps

In the first section, I import the libraries, define helper functions, load the images, and demonstrate image addition and logical union.

### Task 1 — Sampling and quantization

I compare sampling factors of `1`, `2`, `4`, `8`, `14`, and `32`. I then compare quantization levels of `256`, `64`, `16`, `8`, `4`, and `2`.

From my results, I observed that stronger downsampling causes pixelation and loss of spatial detail. I also found that using fewer quantization levels produces visible intensity bands and a loss of tonal detail.

### Task 2 — Arithmetic and set operations

I convert two grayscale images to NumPy arrays and use them to demonstrate:

- Subtraction with wrap-around, saturation, and absolute difference
- Adding a constant value of `175` with clipping
- Grayscale difference, symmetric difference, intersection, and union
- Equivalent logical operations on binary masks of the letters A and B

I highlight an important distinction: ordinary NumPy arithmetic on `uint8` arrays can wrap around, while OpenCV's saturated operations clip values to the valid range of `0–255`.

## Generated files

When I run the notebook, I create these result images in the current working directory:

- `task2_subtraction.png`
- `task2_add175.png`
- `task2_set_difference.png`
- `task2_symmetric_difference.png`
- `task2_intersection.png`

## Notes

- I use nearest-neighbor interpolation when demonstrating sampling so that lost detail and pixelation remain visible.
- I composite the RGBA letter images onto a black background before converting them to grayscale.
- I create binary masks from PNG transparency, where `255` represents the letter and `0` represents the background.
- I avoid a Windows issue in which OpenCV's standard `imread` may fail on paths containing non-English characters. Instead, I read the file bytes with NumPy and decode them with OpenCV.
