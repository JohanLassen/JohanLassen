---
layout: post
read_time: true
show_date: true
title: "[Publication] Deconvoluting 3D peaks in mass spectra"
date: 2024-10-21
img: posts/20241021/bg.png
tags: [feature engineering, preprocessing, optimization]
author: Johan Lassen
description: "My entry into the world of data science in mass spectrometry"
---

In this project I analyzed the optimal way to deconvolute 3D peaks in mass spectra. The results were published in the Analytical Chemistry (ACS) journal. The paper is available [here](https://pubs.acs.org/doi/10.1021/acs.analchem.1c02000). 

The standard output of a mass spectrometry experiment for one sample looks like the plots below and often it takes up between 700 Mb and 1.5 Gb of space. The space requirement is caused by a high density of information, which despite the plots below, is very unstructured and noisy. Figure 1 shows the raw data binned by the plotting software, but in reality the density of information along the peaks landscape is very fluctuating and cannot be represented as images directly from the raw data - the data is not binned like pixels in an image but follows a continous scale. 

Figure 1. Raw data from a mass spectrometry experiment. The x-axis represents the m/z values, the y-axis the retention time, and the z-axis the intensity of the signal. 
<center><img src='./assets/img/posts/20241021/peaks.png' width="540"></center><br>

Because of the complexity, traditional metabolomics (statistical analysis of hundreds to thousands of molecules) aims to deconvolute the peaks into a classical table suitable for e.g., t-tests, correlations, and machine learning. Inspecting the raw data is daunting and the deconvolution can be considered a very naïve way of feature engineering or preprocessing. These processes have a plethora of parameters that should be optimized for each dataset to ensure that we retain as much information as possible.

Now the problem is: 

**The raw data data is so difficult to understand that even setting the parameters for deconvolution is impossible to do perfectly.**

Hence, several packages now apply an optimization to the deconvolution parameters. Especially to packages (IPO and Autotuner, R packages on github) use either brute force optimization or data driven parameter optimization. They both strive to optimize the number of robust peaks that find their way to the feature table.

But we still have a problem:

**No one knows which parameter optimization is the better? Or are any of them better than the default or expert set parameters?**

The fact that we do not know how much information we have to begin with, means that we do also not know how much information we lose in the deconvolution. 

We decided to address this problem using machine learning to assess the information retained in the data (we still do not know how much we lose). So by predicting a label (sex of a fingerprint donor) using the different parameter optimizers and comparing against default and expert set parameters we could assess the information retained in the data. 

In the end the project demonstrated that expert set parameters outperformed the optimization algorithms. I believe that this shows that the deconvolution is fundamentally flawed. In time we will see more advanced methods using end-to-end deep learning that takes in the raw data and directly predicts the labels.
