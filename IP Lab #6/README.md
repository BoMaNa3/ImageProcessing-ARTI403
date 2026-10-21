# My Lab 6: Filtering in the Frequency Domain

ARTI403 Image Processing  
Maan Abdullah Alghamdi  
2240001433

## What I completed

I implemented the manual's frequency-domain Laplacian example and the assessment's Sobel X and Sobel Y filters. I plotted the original image, centered log spectra, signed filter outputs, and combined Sobel magnitude. I verified the Sobel outputs against spatial circular convolution and checked constant-image responses and numerical stability.

## My files

- `Lab_6_Solved.ipynb`: my executed notebook with code, explanations, figures, and numerical outputs.
- `Lab_6_Solved.pdf`: my notebook content and all saved outputs, laid out for reading and printing.
- `images/cameraman.png`: the original 512 x 512 grayscale image from scikit-image `data.camera()`.
- `requirements.txt`: the packages needed to run my notebook in JupyterLab.

## How I run my notebook

I keep the `images` folder beside my notebook. I open a terminal in this folder and use Python 3.10 or newer:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyterlab
```

I open `Lab_6_Solved.ipynb`, select the environment's Python kernel, and choose **Restart Kernel and Run All Cells**. I need internet only for the initial package installation; the notebook loads its image locally. On macOS/Linux I use `.venv/bin/python` instead of `.\.venv\Scripts\python.exe`.

## My implementation choices

I resize the image to 256 x 256 using Pillow Lanczos and scale it to [0, 1]. I bundle the image to avoid runtime dependence on scikit-image downloads. My resizing method differs slightly from the manual's scikit-image resize, but I use the same image consistently for every filter.

I use unshifted FFT arrays for computation and shift spectra only for display. I center the Sobel kernels with `ifftshift` before their FFT. I retain signed convolution responses and combine them with `np.hypot`. My image-sized FFTs use periodic boundaries, so comparisons use circular convolution. Correlation with the same kernels reverses the derivative signs, but leaves the magnitude unchanged.

## My validation and submission

I executed every code cell in a fresh Python kernel and saved the outputs. The assertions in Section 5 verify the calculations and stop execution if a numerical check fails. I can inspect all saved figures and text in the PDF without running Python. My dependency installation must succeed and I must use the correct working directory and kernel when rerunning.

I will upload this lab folder to my GitHub repository and submit its link through Blackboard as the manual requests.
