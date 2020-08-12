---
layout: page
title: Sample workflow
description: Start to finish workflow for data processing and visualization
---

### First things

Start by installing packages

    library(Seurat)
    library(Seurat)
    library(dplyr)
    library(patchwork)
    library(EnhancedVolcano)
    library(ComplexHeatmap)
    library(STRINGdb)
    library(SingleR)
    library(scater)
    library(biomaRt)

*The version of complexheatmap must be 2.2.0

    devtools::install_github('Rohitarora21/SCAS')
    library(advSCvis)
    
### Step 1: run cell cycle scores on whole dataset and save object

### Step 2: Run a set of visualization functions on the whole data
### Step 3: Run user interactive subclustering integration and visualization
### Step 4: Run a set of visualization functions on the subclustered data
