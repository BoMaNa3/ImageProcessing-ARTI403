# Lab #5


Name: Maan Abdullah Alghamdi  
ID: 2240001433  
Course: ARTI 403 - Image Processing

## My work
I used the supplied parrot image to complete the three assessment tasks. I applied a 7 x 7 box filter, compared 5 x 5 and 21 x 21 Gaussian filters, and sharpened the image with a 3 x 3 Laplacian filter. I also implemented the manual's unsharp masking example with sigma 2 and amount 1.5.

I converted the image to RGB and normalized it to float32 before processing. I kept the signed Laplacian response for the sharpening calculation and clipped the final sharpened image to the range from 0 to 1.

## My files
- `Lab5.ipynb`: my notebook with code, explanations, and executed image outputs.
- `Lab5_Notebook.pdf`: a PDF of my notebook, including the code and outputs.
- `Lab5_Report.pdf`: my report with comparisons and explanations.
- `images/parrot.png`: the source image I used.
- `results/`: the comparison figures and filtered images I generated.
- `requirements.txt`: the packages needed to run my notebook.

## How I run my notebook
From the Lab5 folder, I install the dependencies with:

```bash
pip install -r requirements.txt
```

Then I open my notebook with:

```bash
jupyter notebook Lab5.ipynb
```

I select **Restart Kernel and Run All** to reproduce the results.

## What I observed
The box filter softened fine detail. The 21 x 21 Gaussian filter produced more smoothing than the 5 x 5 filter. Laplacian sharpening and unsharp masking enhanced edges, although sharpening can also amplify noise and create halos.

## My submission
I will upload my Lab5 folder to GitHub and submit the repository link through Blackboard, together with the required PDF report.
