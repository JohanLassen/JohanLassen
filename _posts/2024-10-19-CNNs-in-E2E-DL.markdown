---
layout: post
read_time: true
show_date: true
title:  "[Publication] End-to-end deep learning in 1D mass spectra"
date:   2024-10-19
description: End to end deep learning might solve deconvolution issues.
img: posts/20241019/importance.png 
tags: [machine learning, coding, AI, CNN, deep learning]
author: Johan Lassen
mathjax: yes
---

In this study we presented an end-to-end deep learning model that predicts antimicrobial resistance using raw MALDI-MS data, which is one dimensional. 
The one dimension consists of measurement intensities which maps to mass-to-charge ratios of molecules. When the intensities form a peak, we see a molecule, a fragment of a molecule, a protein, a peptide or sometimes just plain noise.

Traditional preprocessing relies on integrating the peaks and to form a tabular dataset with the integrated peaks as features. This is a crude method as it loses a lot of information and significantly decreases the resolution of the data. Additionally, it detaches the data from the raw data, making it harder to backtrack statistical results to the raw data.  

We wanted to answer if we can skip traditional preprocessing (i.e., feature engineering) in 3D mass spectra to directly predict the outome label of the experiment?

In conventional mass spectrometry the peaks of the 3D mass spectra are converted into features in a feature table representing molecules. The molecules can later be used for machine learning or statistical analysis to reveal potential associations to an outcome variable.

As written in the previous post, this feature engineering is flawed as it is too crude and might not capture the complexity of the data. The feature engineering step loses a lot of information.

This might be solved by circumventing the feature engineering step and instead use end-to-end deep learning. Given the use of a correct architecture this method might be able to predict the outcome variable directly from the 3D mass spectra. Furthermore, the resulting model can be backtracked to see which peaks are important for the prediction. This allows a direct comparison between the raw data and the feature importance, enabling full transparency for chemists and biologists.

We set out at a simple starting point, using MALDI data 