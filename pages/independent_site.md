---
layout: page
title: Sample workflow
description: Start to finish workflow for SCENIC output analysis and visualization
---

This sample workflow walks through analysis of SCENIC outputs across two groups (e.g. timepoints, treatments, celltypes). 

### First Steps

Start by installing packages

        library(advSCENICvis)
        library(ggplot2)
        library(dplyr)
        library(AUCell)
        library(tidyr)
        library(tidyverse)
        library(stringr)
        library(ggpubr)
        library(Seurat)
        library(plyr)
        library(tidyverse)
        library(reshape2)
        library(philentropy)
        library(ggrepel)
        library(EnhancedVolcano)

### Step 1: Identify group specific transciption factors (TFs) 

    load(file = "object.Robj")
    
Perform specificity scoring (using Jensen-Shannon divergence): 

    advSCENICvis::specifcityplotting(objectname, regulonAUC, stratvar)
    
Where "objectname" is the name of the Suerat object, "regulonAUC" is the name of the 3.4_regulonAUC SCENIC RDS file output (this .rds file must be in your working directory), and "stratvar" is the name of the variable of the two groups being compared across (must be the same as the name of the column in the Seurat object's metadata). This step returns two plots, one for each of the groups being compared and a CSV document containing specificity scores for every transcription factor for each group. 

Example implementation for a Suerat object named "x", regulonAUC file named "3.4_regulonAUC", and stratifying variabld named "CellType" in the object's metadata:

        advSCENICvis::specifcityplotting("x", "3.4_regulonAUC", "CellType")
    
### Step 2: Identify and visualize differentially enriched TFs (fold change is currently arbitrary) between the two comparison groups 

        advSCENICvis::SCENICvolcano(objectname, regulonAUC, stratvar)
    
The inputs to the SCENICvolcano function are the same as for specificity scoring. This step returns a volcano plot with differentially enriched TFs in red (and all other TFs in blue) as well as a CSV stats file containing p values and average log fold change values for every TF. Note, if the stratifying variable contains more than two unique groups, then this function will create volcano plots/stats files for all unique pairwise group comparisons. 

Example implementation for a Suerat object named "x", regulonAUC file named "3.4_regulonAUC", and stratifying variabld named "CellType" in the object's metadata:

        advSCENICvis::SCENICvolcano("x", "3.4_regulonAUC", "CellType")

### Step 3: Visualize AUC value distributions of TFs using histograms and violin plots

    advSCENICvis::SCENICplots(object, split.by, regulonAUC)

The inputs to this function are similar to before. "object" is the name of the Seurat object, "split.by" is the name of the stratyfing variable, and "regulonAUC" is the name of the 3.4_regulonAUC SCENIC RDS file output (.rds file needs to be in the working directory). This function creates two new directories, one for plot outputs with p values for all pairwise group comparisons, and the other for plot outputs without p values. For each transcription factor, an original and lognormally transformed histogram and violin plot are created; both plot types are split by the stratifying variable. Steps 1 and 2 can be used to inform which TF plots are of most interest for further analysis. 

Example implementation for a Suerat object named "x", regulonAUC file named "3.4_regulonAUC", and stratifying variabld named "CellType" in the object's metadata:

        advSCENICvis::SCENICvolcano("x", "CellType", "3.4_regulonAUC")

### Step 4: Plot global transcription factor activtion for groups of interest

        advSCENICvis::GlobalHistograms(object, split.by, regulonAUC)
       
The inputs to this function are the same as in Step 3. The output of this step are two histograms (original and lognormally transformed) that plot AUC score density across all TFs in the dataset. Once again, these plots are split by the stratifying variable. Although this plot cannot directly inform which TFs are contributing to the AUC scores depicted, it can be helpful in comparing global transcription factor activation across the groups of interest. 

### Step 5: Interactive visualization of data

        advSCENICvis::AUCVisualizer(strat, Xobj = "x.Robj",tSNE = "tSNE_AUC_50pcs_50perpl.Rds",scenicOptions = "scenicOptions.Rds",PathToRegulonAUC = "3.4_regulonAUC.Rds",      PathToCellInfo = "cellInfo.Rds")
        
To use the default inputs to the AUCVisualizer function (shown above), enter the name of the stratifying variable as the only arguement. Otherwise, specify the arguments using the names of the files in your working directory. scenicOptions.Rds is a SCENIC input; tSNE_AUC_50pcs_50perpl.Rds, 3.4_regulonAUC.Rds are SCENIC outputs, and cellInfo.Rds contains columns of the Seurat object metadata of stratifying variables of interest. All .Rds files must be in the working directory. 
