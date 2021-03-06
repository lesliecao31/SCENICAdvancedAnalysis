---
layout: page
title: Advanced SCENIC analysis and visualization 
tagline: Unbiased regulon activation analysis of SCENIC data across multiple groups
description: Minimal tutorial on making a simple website with GitHub Pages
---

SCENIC performs gene-regulatory network inference: [familiarize yourself with SCENIC](https://www.nature.com/articles/nmeth.4463). This analysis must be run after intalling and running SCENIC on dataset and is specific to Seurat objects: [visit the installation tutorial](https://rawcdn.githack.com/aertslab/SCENIC/701cc7cc4ac762b91479b3bd2eaf5ad5661dd8c2/inst/doc/SCENIC_Setup.html), [visit the SCENIC tutorial](https://rawcdn.githack.com/aertslab/SCENIC/0a4c96ed8d930edd8868f07428090f9dae264705/inst/doc/SCENIC_Running.html#scenic_workflow).


This workflow will:
- Identify group specific transcription factors (TFs) through Jensen–Shannon divergence
- Identify differentially enriched TFs between all pairwise group comparisons and visualize using volcano plots
- Visualize AUC value distributions of group specific/differentially enriched TFs using histograms and violin plots
- Plot global transcription factor activation of groups of interest
- Interactive visualization of downstream gene targets and TF activation using RShiny 

---

- [Adding SCENIC tSNE embeddings to Seurat object](pages/overview.html)
- [Sample Workflow With Two Groups](pages/independent_site.html)
- [Differential downstream target analysis](pages/resources.html)
- [Monocle3 integration with SCENIC](pages/project_site.html)

---
If anything here is confusing (or _wrong_!), or if we've missed
important details, please send an email to leslie.cao@alumni.ubc.ca and rohit.arora2@ucalgary.ca

