---
layout: page
title: SingleR annotation on Seurat Data
description: simple annotation using the function: singleRvisualization() 
---

Simple annotation of data using the singleRvisualization function.

This tutorial walks through an alignment of two groups of PBMCs from Kang et al, 2017. In this experiment, PBMCs were split into a stimulated and control group and the stimulated group was treated with interferon beta. The response to interferon caused cell type specific gene expression changes that makes a joint analysis of all the data difficult, with cells clustering both by stimulation condition and by cell type.

    library(Seurat)
    library(SeuratData)
    library(cowplot)
    library(patchwork)
