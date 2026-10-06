# Lab 4: Intensity Transformations and Filtering — Spatial Domain

**Student:** Maan Abdullah Alghamdi  
**Student ID:** 2240001433  
**Course:** ARTI 404 — Image Processing

## Overview

In this lab, I explore image intensity transformations using NumPy, Matplotlib, and scikit-image. I compare original and transformed images through visualizations, histograms, and cumulative histograms.

I focus on intensity transformations in these exercises. I have not implemented spatial filtering in this notebook.

## Notebook

`Lab_4_Maan_Abdullah_Alghamdi_2240001433.ipynb`

## Exercises

| Exercise | Method | Image / Parameters |
| --- | --- | --- |
| Procedural Task 1 | Fixed binary thresholding | Moon; thresholds 0, 50, 100, 150, and 200 |
| Procedural Task 2 | Percentile contrast stretching | Moon; 2nd–98th percentiles |
| Assessment Task 1 | Percentile contrast stretching | Moon; 3rd–80th percentiles |
| Assessment Task 2 | Histogram equalization | Moon; output intensities in the range 0–1 |
| Assessment Task 3 | Histogram matching | Chelsea source matched to the Rocket reference, independently for each RGB channel |

I use assertions to check binary output values, image dimensions, intensity ranges, and finite histogram-matching results.

## Requirements

- Python 3 (the notebook metadata records Python 3.12.10)
- Jupyter Notebook or JupyterLab
- NumPy
- Matplotlib
- scikit-image

I install the required packages with:

```bash
python -m pip install notebook numpy matplotlib scikit-image
```

## How to Run

1. I save the notebook in my working directory.
2. I open a terminal in that directory and start Jupyter:

   ```bash
   jupyter notebook
   ```

3. I open `Lab_4_Maan_Abdullah_Alghamdi_2240001433.ipynb`.
4. I select the Python 3 kernel and run all cells from top to bottom.

I use the built-in scikit-image sample images `moon`, `rocket`, and `chelsea`, so I do not need to supply external images. If a sample image is not cached, scikit-image may download it on first use.

## Outputs

When I run the notebook, I create an `images/` folder relative to the kernel's working directory and save these original sample images:

```text
images/
├── moon.png
├── rocket.png
└── chelsea.png
```

I display the transformed images and histogram plots inside the notebook. In my final validation cell, I print `All result checks passed.` when all assertions succeed.

## Key Observations

- I observe that higher binary thresholds retain fewer white pixels.
- I use percentile stretching to expand the selected intensity interval and clip values outside it.
- I observe that the 3rd–80th percentile stretch saturates more bright pixels than the 2nd–98th percentile stretch.
- I observe that histogram equalization uses a nonlinear mapping and does not guarantee a perfectly flat histogram.
- I use histogram matching to preserve Chelsea's spatial content while shifting its per-channel intensity distributions toward Rocket's.

