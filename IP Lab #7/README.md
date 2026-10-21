# Lab #7

Name: Maan Abdullah Alghamdi  
ID: 2240001433  
Course: ARTI 403 - Image Processing

## What I completed

I completed Part A (Laplacian sharpening) and Part B (mathematical and statistical
filters). My executed notebooks include the code, figures, explanations and checks.
The matching PDFs contain the notebook text, code and saved outputs.

## How I run my work

1. I keep both notebooks and all three JPG images in the same folder.
2. I use Python 3.10 or newer. In a terminal opened in this folder, I run:

   ```sh
   python -m pip install -r requirements.txt
   python -m notebook
   ```

3. I open either completed notebook, select a Python 3 kernel, and choose
   **Restart Kernel and Run All Cells**. Each notebook works independently.
4. I check the final cell for the message that all checks passed.

## My approach

In Part A, I retain the signed Laplacian in floating point and subtract it from
the original because the kernel has a negative centre. I clip before converting
to uint8. I also compare the manual kernel with OpenCV and include Gaussian
prefiltering as a separate sharpening example.

In Part B, I generate repeatable Gaussian, salt-and-pepper, exponential and uniform
noise with seed 2240001433. I apply arithmetic, geometric, harmonic,
contraharmonic, median, maximum, minimum and midpoint filters. I demonstrate the
sign of the contraharmonic order using separate salt-only and pepper-only inputs.
I also filter the supplied salt&Pepper.jpg with the median filter.

I compare all nine filter settings across the four generated noise types using
MSE and PSNR against noise.jpg before adding synthetic noise. I treat that image
as a reference, without assuming its original contents are noise-free. I do not
calculate restoration scores for the supplied impulse image without a clean pair.

## My checks

I ran both notebooks from fresh kernels in their deliverable folder. I checked
output shape and type, arithmetic-method agreement, Laplacian equivalence,
constant and zero inputs, known neighbourhood results, clipping, seed
repeatability, and contraharmonic special cases. I inspected both PDF exports
for readable code and complete figures. Package versions used in execution appear
in the setup output of each notebook. Other environments need the listed dependencies.

## Files I included

- Lab_7_A_Completed.ipynb and Lab_7_A_Completed.pdf
- Lab_7_B_Completed.ipynb and Lab_7_B_Completed.pdf
- moon.jpg, noise.jpg and salt&Pepper.jpg
- requirements.txt and this README.md
