---
layout: page
title: Advanced Single Cell Analysis with Seurat
tagline: Unbiased single cell analysis of integrated single-cell data
description: Minimal tutorial on making a simple website with GitHub Pages
---

Unbiased analysis of integrated data with Seurat. Analyis must be done post quality control: [visit the tutorial](https://satijalab.org/seurat/v3.2/pbmc3k_tutorial)
and post integration: [visit the tutorial](https://satijalab.org/seurat/v3.2/immune_alignment)

The first half of this workflow will:
- Use singleR to investigate celltypes in a dataset
- Create piecharts on celltype distributions (and statistically quantify these differences)
- Visualize cellcycle scoring on celltypes
- Visualize correlations in gene expression between two groups
- Find correlated networks of protiens that differ in celltypes between two groups using stringDB v10.0
- Perform clustree analysis on data

The second half of this workflow will:
- Integrate and recluster celltypes in order to investigate changes on a more granular level. Perform all analyses that were done on the global scale on each subcluster as well as create volcano plots.

If you would like to see the outputs of this analysis, they are available at: [Visit the dropbox](https://www.dropbox.com/sh/ntabbv6rzb431um/AADFXA1voHhXvqK7dEqApYQEa?dl=0)

---

- [Using SingleR](pages/overview.html)
- [Sample Workflow](pages/independent_site.html)

---
If anything here is confusing (or _wrong_!), or if we've missed
important details, please send an email to rohit.arora2@ucalgary.ca and leslie.cao@alumni.ubc.ca

