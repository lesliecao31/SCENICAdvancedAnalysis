---
layout: page
title: SingleR annotation on Seurat Data
description: simple annotation using the function singleRvisualization
---

Simple annotation of data using the singleRvisualization function.

This tutorial walks through an alignment of two groups of PBMCs from Kang et al, 2017. In this experiment, PBMCs were split into a stimulated and control group and the stimulated group was treated with interferon beta. The response to interferon caused cell type specific gene expression changes that makes a joint analysis of all the data difficult, with cells clustering both by stimulation condition and by cell type.
(https://satijalab.org/seurat/v3.2/pbmc3k_tutorial.html)

This object has been generated from the following Seurat walkthrough: [visit the tutorial]https://satijalab.org/seurat/v3.2/pbmc3k_tutorial.html

These outputs can be found at: under: Overall analysis of data in the SingleR folder.

Clustering of data using singleR:

        library(SingleR)
        library(Seurat)
        library(scater)
        devtools::install_github('Rohitarora21/SCAS')
        library(advSCvis)
        advSCvis::singleRvisualization("object","h")
        
The function singleRvisualization will return two plots. One is created from single cell data, and the other is microarray based. If you wish to run it using a human reference please use: advSCvis::singleRvisualization("object","h"), for mouse please use: advSCvis::singleRvisualization("object","m").

It is also important to note that singleR has much more utility when data is more heterogeneous in celltype.

SingleR outputs can be found at: under: [visit singleR results]https://www.dropbox.com/sh/ntabbv6rzb431um/AADFXA1voHhXvqK7dEqApYQEa?dl=0 at outputs under overall analysis of data



