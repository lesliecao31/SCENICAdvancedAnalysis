---
layout: page
title: SCENIC tSNE embeddings
description: adding SCENIC tSNE embeddings to Seurat object
---

Add SCENIC tSNE embeddings to Seurat object.

SCENIC performs T-distributed Stochastic Neighbor Embedding (tSNE) method of dimensionality reduction. This tutorial walks how to add tSNE embeddings to the Seurat object that SCENIC was performed on. It adds a reduction called "scenic" and creates two new columns in the object's metadata for the first two tSNE principle components.

Seurat objects can be created from the following walkthrough: [visit the tutorial](https://satijalab.org/seurat/v3.2/pbmc3k_tutorial.html)

Adding SCENIC tSNE embeddings:

                advSCENICvis::SCENICembeddings("object", "tSNE")
                
The "object" input is the name of the Seurat object. The "tSNE" input is the name of the 50pcs, 50perpl RDS file output from SCENIC (the .rds file must be in your working directory). 


