# PCA vs. Autoencoder for Dimensionality Reduction and Visualization of RNASeq Dataset


Write a 3-4 sentence abstract. It should introduce the problem and your approach. You may also want some numbers like 35 mAP and 78% accuracy. You can use this example README for your project, you can use a different ordering for your website, or you can make a totally different website altogether!

VIDEO GOES HERE (probably): Record a 2-3 minute long video presenting your work. One option - take all your figures/example images/charts that you made for your website and put them in a slide deck, then record the video over zoom or some other recording platform (screen record using Quicktime on Mac OS works well). The video doesn't have to be particularly well produced or anything.

## Problem Statement

Dimensionality reduction is a crucial step in the overall genome sequencing data analysis workflow. Common techniques include PCA, t-SNE, and UMAP, which are popular for their ability to produce two-dimensional representations that are easily visualizable. I was interested in seeing if an autoencoder architecture would be able to do a better job than PCA, specifically when applied to high-dimensional RNAseq data spanning across multiple cancer types.  

## Related Work

Other people are out there doing things. What did they do? Was it good? Was it bad? Talk about it here.

I used the TCGA Pan-Cancer Atlas RNASeq dataset(https://gdc.cancer.gov/about-data/publications/pancanatlas). It includes expression values for 20,531 genes across 11,069 tumor samples. 33 cancer types are represented. I focused on the 9 cancer types which had 500 or more samples each.

## Methodology

I opted to utilize an autoencoder framework to achieve dimensionality reduction. An autoencoder attempts to recreate the input it's given as accurately as possible after that input has been fed through any number of hidden layers. The representation learned by the encoder portion can then be used for downstream purposes, like visualization if the final number of features are 2 or 3.

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

