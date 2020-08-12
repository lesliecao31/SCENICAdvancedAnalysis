---
layout: page
title: Sample workflow
description: Start to finish workflow for data processing and visualization
---
### All visualization outputs are available at:
### All code is available at:

### First Steps

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
    library(clustree)
    library(ggplot2)

*The version of complexheatmap must be 2.2.0

    devtools::install_github('Rohitarora21/SCAS')
    library(advSCvis)
    
In this example, we will be using a dataset of two groups of PBMCs from Kang et al, 2017. These two groups have been split by a column in metadata in the seurat object called: "stim", celltype annotations are stored in: "celltypes", and the object is saved as "object".

### Step 1: Run cell cycle scores on whole dataset and save object

    load(file = "object.Robj")
    
Make sure to set the default assay to RNA. 

    DefaultAssay(object) = "RNA"
    
For mouse data:

    m.s.genes <- advSCvis::convertHumanGeneList(cc.genes.updated.2019$s.genes)
    m.g2m.genes <- advSCvis::convertHumanGeneList(cc.genes.updated.2019$g2m.genes)
    object <- CellCycleScoring(object,s.features = m.s.genes, 
                              g2m.features = m.g2m.genes, 
                              set.ident = TRUE)
    save(object, file = "object.Robj")
    
for human data:
    m.s.genes <- cc.genes$s.genes
    m.g2m.genes <- cc.genes$g2m.genes
    object <- CellCycleScoring(object, s.features = m.s.genes, 
                          g2m.features = m.g2m.genes, 
                          set.ident = TRUE)
    save(object, file = "object.Robj")
    
### Step 2: Run a set of visualization functions on the whole data (Outputs under overall analysis of data in dropbox) 

    advSCvis::CellCyclevis("object","celltypes","stim")
    advSCvis::piechartvisualizer("object","celltypes","stim")
    advSCvis::chisquaredtest("object","celltypes","stim")
    advSCvis::clustreeplot("object")
    advSCvis::correlationplots("object","celltypes","stim")
    
Optional step to visualize protien interactions of thirty signature genes:

If human:

    advSCvis::stringDBvis("object","celltypes","stim","h") 
    
If mouse:

    advSCvis::stringDBvis("object","celltypes","stim","m") 
    
### Step 3: Run user interactive subclustering integration and visualization (Outputs under: Analysis of all reclustered celltypes)
Choose cells that have > 20 cells from each group to recluster:

    celltypes <- list("CD14 Mono","CD4 Memory T","T activated" ,"CD4 Naive T", 
                  "Mk", "B Activated", "B","DC",            
                  "CD16 Mono","NK","CD8 T")

Now we integrate and subcluster. The code below will need to be modified for each dataset that it is run on. It will allow users to recluster and reintegrate all of their celltypes prior defined. An elbow plot will come up on the plots section of the screen and the user will enter in the number of PC's desired from the elbow plot. This is a long step that is very computationally intensive and will take approx. 3-20 minutes depending on the size of the seurat object. If this step is confusing to any, please feel free to reach out to rohit.arora2@ucalgary.ca and lesliecao4@gmail.com. The outputs of this code will be made for each celltype and include the object either integrated or reclustered (if it is large enough to be integrated then integrated, if not then reclustered), as well as a umap of seurat clusters, a umap split by group, and a umap grouped by group. This loop will return a folder for each celltype passed in as a list.

### Step 4: Run a set of visualization functions on the subclustered data (Outputs Under: Analysis of all reclustered celltypes in each celltype folder)

Run this code in the working directory with all the new folders generated from step 3:

    for (celltype in celltypes){
      setwd(celltype)
      CreateVolcanoPlot("x","stim","CTRL","STIM")
      piechartvisualizer("x","seurat_clusters","stim")
      correlationplots("x","seurat_clusters","stim")
      clustreeplot("x")
      chisquaredtest("x","seurat_clusters","stim")
      CellCyclevis("x","seurat_clusters","stim")
      setwd('..')
    }

