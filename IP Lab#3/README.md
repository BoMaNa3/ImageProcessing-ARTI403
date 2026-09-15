# ARTI 404 — Image Processing Lab 3

**Student:** Maan A Alghamdi — 2240001433

This repository contains my Jupyter notebook, `Lab_3_Maan_Alghamdi.ipynb`, for **ARTI 404: Image Processing**. In this lab, I use the OpenCV library to read, save, and convert images between color spaces, and then I apply geometric and intensity transformations to an image.

## My learning outcomes

- Explain how digital images are represented and manipulated in a computer.
- Apply geometric transformations to images.

## What I covered

- Reading an image with OpenCV and inspecting it as a NumPy array (type, shape, `uint8` values, BGR order)
- Loading an image directly in grayscale
- Saving an image to disk and reading it back
- Converting between color spaces (BGR → Grayscale, BGR → YUV) and viewing the Y, U, and V channels
- Geometric transformations:
  - Scaling (enlarging ×2)
  - Rotation by 120°
  - Horizontal and vertical shear
- Intensity transformations:
  - Negative image
  - Log transformation
  - Power-law (gamma) transformation
- Handling image paths containing non-English characters on Windows

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab
- NumPy
- OpenCV
- Matplotlib

Install the required packages with:

```bash
pip install notebook numpy opencv-python matplotlib
```

## Input images I used

I used the following files in an `images` folder:

```text
images/
├── fruits.jpg
└── building.jpg
```

- `fruits.jpg` is a colorful photo, which I used for Steps 1–4 (grayscale and YUV channels).
- `building.jpg` is a dark night photo of a city skyline. I used it for both tasks: its straight edges make rotation and shear easy to see, and its dark tones make the log and gamma transformations visible.

My notebook first looks for `images` next to the notebook, then `../images`, and finally a Windows fallback path on my Desktop.

## How to run

1. I open `Lab_3_Maan_Alghamdi.ipynb` in Jupyter Notebook or JupyterLab.
2. I confirm that the input images are available in the `images` folder.
3. I run all cells from top to bottom.

From a terminal, Jupyter Notebook can be started with:

```bash
jupyter notebook Lab_3_Maan_Alghamdi.ipynb
```

## Lab structure

### Steps 1–4 — OpenCV basics

I read `fruits.jpg` with `cv2.imread`, print its type and shape, load it in grayscale with `cv2.IMREAD_GRAYSCALE`, save it with `cv2.imwrite`, and convert it with `cv2.cvtColor`. I also list the available `COLOR_` conversion flags and display the three YUV channels separately.

### Task 1 — Geometric transformations

- **Scaling:** I enlarge the image by a factor of `2` with `cv2.resize` (612×459 → 1224×918) and compare `INTER_NEAREST` with `INTER_CUBIC` interpolation on a zoomed crop.
- **Rotation:** I rotate the image by `120°` with `cv2.getRotationMatrix2D` and `cv2.warpAffine`. I show the result on the original canvas (corners cut off) and on an enlarged canvas that keeps the whole image.
- **Shear:** I apply a horizontal shear (`sh_x = 0.4`) and a vertical shear (`sh_y = 0.3`) using affine matrices, widening the output so nothing is cut off.

### Task 2 — Intensity transformations

I apply each transformation to the grayscale version of `building.jpg` and measure contrast using the standard deviation of the pixel values.

- **Negative:** `s = 255 − r`
- **Log:** `s = c · log(1 + r)`, with `c = 255 / log(1 + r_max) ≈ 46`, so the brightest pixel maps to `255`. I also compare a smaller and a larger `c` to show why this value is appropriate.
- **Power law:** `s = 255 · (r / 255)^γ`. I test several gamma values and choose the one with the highest contrast, which is `γ = 0.7`.

From my results, I observed that the log transformation reveals detail in the dark streets and sky, but slightly lowers the overall contrast (43.6 → 38.8) because it compresses the bright city lights. The power-law transformation with `γ = 0.7` increases the contrast (43.6 → 45.3), while `γ > 1` makes this dark image even darker.

I finish the task with a plot of all the transformation curves, the results side by side, and their histograms.

## Generated files

When I run the notebook, I create this file in the `images` folder:

- `output.jpg` — the grayscale version of `fruits.jpg` (Step 3)

## Notes

- I display images inline with Matplotlib instead of `cv2.imshow`, which opens a separate window and can freeze the Jupyter kernel. I convert color images from BGR to RGB before displaying them.
- The manual's `print [x for x in dir(cv2) if x.startswith('COLOR_')]` is Python 2 syntax, so I use `print(...)` for Python 3.
- I avoid a Windows issue in which OpenCV's standard `imread` and `imwrite` may fail on paths containing non-English characters. In that case, I read and write the file bytes with NumPy and decode or encode them with OpenCV.
