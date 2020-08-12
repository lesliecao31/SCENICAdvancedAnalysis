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
    
In this example, we will be using a dataset of two groups of PBMCs from Kang et al, 2017. These two groups have been split by a column in metadata in the seurat object called: "stim", celltype annotations are stored in: , and object is saved as "object".

### Step 1: Run cell cycle scores on whole dataset and save object

    load(file = object.Robj)
    
For mouse data:

    m.s.genes <- advSCvis::convertHumanGeneList(cc.genes.updated.2019$s.genes)
    m.g2m.genes <- advSCvis::convertHumanGeneList(cc.genes.updated.2019$g2m.genes)
    object <- CellCycleScoring(object,s.features = m.s.genes, 
                              g2m.features = m.g2m.genes, 
                              set.ident = TRUE)
    save(object, file = "object.Robj")
    
for human data:

    s.genes <- cc.genes$s.genes
    g2m.genes <- cc.genes$g2m.genes
    object <- CellCycleScoring(object, s.features = m.s.genes, 
                          g2m.features = m.g2m.genes, 
                          set.ident = TRUE)
    save(object, file = "object.Robj")
    
### Step 2: Run a set of visualization functions on the whole data

    advSCvis::CellCyclevis("object","celltypes","stim")
    advSCvis::piechartvisualizer("object","celltypes","stim")
    advSCvis::chisquaredtest("object","celltypes","stim")
    advSCvis::clustreeplot("object")
    advSCvis::correlationplots("object","celltypes","stim")
    
Optionally to visualize protien interactions:
If human:

    advSCvis::stringDBvis("object","celltypes","stim","h") 
    
If mouse:

    advSCvis::stringDBvis("object","celltypes","stim","m") 
    
### Step 3: Run user interactive subclustering integration and visualization
### Step 4: Run a set of visualization functions on the subclustered data
