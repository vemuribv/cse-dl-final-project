# PCA vs. Autoencoder for Dimensionality Reduction and Visualization of RNASeq Dataset

This project aims to demonstrate the ability of an autoencoder framework to learn an informative low-dimensional representation of a high-dimensional dataset and use this encoding to generate a visualization that (qualitatively) outperforms PCA. I chose a gene expression dataset with over 17,000 features (genes) and several thousand samples. My network included six hidden layers in the encoder and six in the decoder (the same layers but in reverse). After 500 epochs with a learning rate of 0.001, I was able to achieve a final loss of 0.4383, but the visualization was actually better after 150 epochs with a slightly higher loss (0.5124).

VIDEO GOES HERE (probably)

## Problem Statement

Dimensionality reduction is a crucial step in the overall genome sequencing data analysis workflow. Common techniques include PCA, t-SNE, and UMAP, which are popular for their ability to produce two-dimensional representations that are easily visualizable. I was interested in seeing if an autoencoder architecture would be able to do a better job than PCA, specifically when applied to high-dimensional RNAseq data spanning across multiple cancer types.  

## Related Work

I took inspiration from:
- Chaudhary 2018: Deep Learning–Based Multi-Omics Integration Robustly Predicts Survival in Liver Cancer
- Tan 2015: UNSUPERVISED FEATURE CONSTRUCTION AND KNOWLEDGE EXTRACTION FROM GENOME-WIDE ASSAYS OF BREAST CANCER WITH DENOISING AUTOENCODERS
- Lin 2020: A deep adversarial variational autoencoder model for dimensionality reduction in single-cell RNA sequencing analysis

The Lin 2020 paper in particular is very thorough in its approach to benchmarking their proposed model against many others. I attempted a more simplified version that I felt comfortable with and applied it to a well-known public dataset (TCGA PanCan) that I was interested in.

The TCGA Pan-Cancer Atlas RNASeq dataset(https://gdc.cancer.gov/about-data/publications/pancanatlas) includes expression values for 20,531 genes across 11,069 tumor samples. 33 cancer types are represented. I focused on the 9 cancer types which had 500 or more samples each. After some standard preprocessing, I was left with 5,726 samples and 17,475 genes.

Number of cancer types: 9
Number of samples per cancer type:
BRCA    1215
KIRC     606
LUAD     576
THCA     572
HNSC     566
UCEC     555
LUSC     553
PRAD     550
LGG      533

## Methodology

I opted to utilize an autoencoder framework to achieve dimensionality reduction. An autoencoder attempts to recreate the input it's given as accurately as possible after that input has been fed through any number of hidden layers that are successively more restrictive. The representation learned by the encoder portion can then be used for downstream purposes, like visualization, if the final number of features are 2 or 3.

Since the goal was to compare the two methods via a 2d visualization, the final layer of the encoder portion needed to have 2 nodes. With that goal in mind, I built backwards and successively increased the number of nodes in each layer until I reached something close to the input size. I attempted to achieve a systematic bottleneck over multiple layers rather than a rapid one that may have resulted in too much loss of information.


How did you decide to solve the problem? What network architecture did you use? What data? Lots of details here about all the things you did. This section describes almost your whole project.

Figures are good here. Maybe you present your network architecture or show some example data points?

## Experiments/Evaluation

Initially I had planned to use INSERT LINK as an empirical way of determining whether PCA or the autoencoder resulted in a kmeans clustering that was closed to ground truth. However, I found that outside of 2-3 clusters/cancer types, there was too much overlap between types to realistically match a predicted cluster to a ground truth cluster. 

## Results

The autoencoder itself achieved a final loss of INSERT after 5 epochs of training.

I settled on visualization between the two competing methods to determine which may have the better performance for this use case. 

How well did you do? What are you comparing to? Maybe you want ablation studies or comparisons of different methods.

You may want some qualitative results and quantitative results. Example images/text/whatever are good. Charts are also good. Maybe loss curves or AUC charts. Whatever makes sense for your evaluation.

## Discussion

You can talk about your results and the stuff you've learned here if you want. Or discuss other things. Really whatever you want, it's your project.

