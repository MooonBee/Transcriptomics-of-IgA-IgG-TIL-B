# Comparative transcriptome analysis of B lymphocyte populations infiltrating tumors and expressing IgA and IgG

## Brief description
This repository contains code, tables, and visualizations for a paper soon to be published by Chudakov Lab. The research focuses on investigating the role of tumour-infiltrating memory B cells in Lung Adenocarcinoma (LUAD) and Kidney Renal Clear Cell Carcinoma (KIRC) progression. The findings shed light on the specific subset of FCRL4-expressing memory B cells, indicating exhausted, chronically antigen-stimulated phenotype.

## Repository structure

### Bulk 

Contains scripts for downstream analysis of IgA+ vs IgG+ memory B cells in LUAD and KIRC. The bulk transcriptome libraries obtained in our laboratory will be made available after the release of the associated article. 
The raw data were processed using STAR and featureCounts. GRCh38.p13 genome assembly and GRCh38.109 gene annotation from ensembl.org were used.

[**1_Lcp.R**](/Bulk/R_scripts/1_Lcp.R) 

Deconvolution was performed for identification of contaminated samples in LUAD. The results were validated by the expression of CD19 and CD20 (MS4A1) marker genes.
<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Lcp_heatmap_xCell.png"  width=45% height=45%/>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Lcp_scatterplot_CD19_vs_CD20.png"  width=45% height=45%"/>
    
Differential expression of IgA+ vs IgG+ memory B cells and shrinkage of log2 fold changes we have identified 46 differentially expressed (DE) genes with adjusted P value (p_adj) < 0.01 and absolute log fold change (LFC) > 1. [(List of DE genes)](/Bulk/Tables/Lcp_DE_genes.tsv)

<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Lcp_heatmap_DE_genes.png"  width=45% height=45%/>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Lcp_volcano_plot_DE_genes.png"  width=45% height=45%"/>

To detect statistically significant group of genes Gene Set Enrichment Analysis supplemented with Gene ontology (GO) gene sets, some paths in the graph have been removed. [(List of DE pathways)](/Bulk/Tables/Lcp_gsea_combined_results.tsv)

<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Lcp_GSEA_summary.png" width=60% height=60%>

[**2_Rcp.R**](/Bulk/R_scripts/2_Rcp.R) 

Deconvolution and valisation for identification of contaminated samples was performaed also for KIRC.

<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Rcp_heatmap_xCell.png"  width=45% height=45%/>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Rcp_scatterplot_CD19_vs_CD20.png"  width=45% height=45%"/>

Differential expression of IgA+ vs IgG+ memory B cells and shrinkage of log2 fold changes we have identified 6 DE genes with p_adj < 0.05 and absolute LFC > 1. [(List of DE genes)](/Bulk/Tables/Rcp_DE_genes.tsv)

<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Rcp_heatmap_DE_genes.png"  width=45% height=45%/>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Rcp_volcano_plot_DE_genes.png"  width=45% height=45%/>


Gene Set Enrichment Analysis supplemented with Gene ontology (GO) gene setswas also used. [(List of DE pathways)](/Bulk/Tables/Rcp_gsea_combined_results.tsv)

<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Bulk/Graphs_png/Rcp_GSEA_summary.png" width=70% height=70%>

### Single-cell

Contains scripts for clusterization and description of tumour-infiltrating memory B cells in LUAD. The single-cell transcriptome data was obtained from Leader et al. [article](https://github.com/effiken/Leader_et_al).
Data were aligned by the authors of the article using Cell Ranger.

[**1_Labels.R**](/Single-cell/R_scripts/1_Labels.R) 

Addition of metadata and exclusion of TCR samples

[**2_DoubletFinder.R**](/Single-cell/R_scripts/2_DoubletFinder.R)

Detection of doublets using [DoubletFinder](https://github.com/chris-mcginnis-ucsf/DoubletFinder) package.

[**3_QC.R**](/Single-cell/R_scripts/3_QC.R)

Addition of QC metrics (such as % of motochondrial, ribosomal, and hemoglobin genes, % of the largest genes etc.)

[**4_QC_graphs.R**](/Single-cell/R_scripts/4_QC_graphs.R)

Visualization of QC metrics and filtering of inappropriate cells.

<p align="center">
<img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Single-cell/Graphs_png/4_QC_vln_nFeature_RNA.png" width=70% height=70%>

<p align="center">
<img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Single-cell/Graphs_png/4_QC_dotplot_mito_ribo_feature.png" width=70% height=70%>

[**5_clusterization_of_all_cells.R**](/Single-cell/R_scripts/5_clusterization_of_all_cells.R)

Clusterization of all cells.

[**6_visualization_of_all_cells.R**](/Single-cell/R_scripts/6_visualization_of_all_cells.R)

visualization of all cells, identification of doublets, and ground identification of B cells.

<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Single-cell/Graphs_png/6_DimPlot_clusters.png"  width=45% height=45%/>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Single-cell/Graphs_png/6_DimPlot_doublet_finder.png"  width=45% height=45%/>
    <br>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Single-cell/Graphs_png/6_FeaturePlot_MS4A1.png"  width=45% height=45%/>
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/Single-cell/Graphs_png/6_FeaturePlot_CD3E.png"  width=45% height=45%/>

### TCGA

Contains script for Kaplan-Meier curves representing the influence of absolute and normalized value of FCRL4 gene to the progression of LUAD. 
<p align="center">
    <img src="https://github.com/EvgeniyShchoka/Transcriptomics-of-IgA-IgG-TIL-B/blob/master/TCGA/Graphs_png/surv_plot_normalized_small.png" width=50% height=50%>


