---
layout: page
title: SingleR annotation on Seurat Data
description: simple annotation using the function: singleRvisualization() 
---
Simple annotation of data using the singleRvisualization function.

Here, we analyze a dataset of 8,617 cord blood mononuclear cells (CBMCs), produced with CITE-seq, where we simultaneously measure the single cell transcriptomes alongside the expression of 11 surface proteins, whose levels are quantified with DNA-barcoded antibodies. First, we load in two count matrices : one for the RNA measurements, and one for the antibody-derived tags (ADT).

  library(Seurat)
  library(ggplot2)
  library(patchwork)
