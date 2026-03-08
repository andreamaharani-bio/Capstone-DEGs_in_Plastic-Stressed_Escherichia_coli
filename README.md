# Capstone-DEGs_in_Plastic-Stressed_Escherichia_coli
Analysis of differentially expressed genes (DEGs) in E. coli derived from plastic-stress response and their potential as biomarkers for future metagenomic detection

**Overall workflow:** GEO Dataset → GEO2R Processing → Data Cleaning (R) → Exploratory Analysis → Differential Expression Analysis → Visualization (PCA, Volcano, Heatmap) → Identification of Candidate Biomarkers

**Project Overview**
This project performs a transcriptomic analysis of Escherichia coli gene expression profiles under different experimental conditions related to conjugation-associated stress and reactive oxygen species (ROS).

The analysis workflow integrates GEO2R preprocessing with downstream statistical and visualization analysis in R. The primary goal is to identify differentially expressed genes (DEGs) and explore their potential role as molecular biomarkers associated with stress responses during bacterial conjugation.

The results provide insights into transcriptional changes that may indicate key regulatory pathways and candidate genes involved in oxidative stress adaptation and conjugation efficiency.

**Dataset Description**
**a. Data Source**
The dataset used in this project was obtained from the NCBI Gene Expression Omnibus (GEO) database.
link here: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE248909

Dataset accession: GSE248909

> This dataset contains RNA-seq transcriptomic profiles of Escherichia coli LE392 under conditions designed to investigate the role of reactive oxygen species (ROS) in bacterial conjugation processes.

Raw sequencing data were processed and analyzed using GEO2R, which applies the limma statistical framework to compute gene-level expression differences.

The processed data include log2 fold change (log2FC) expression values for thousands of genes across multiple samples.

**Project Objective**
The primary objective of this project is to identify differentially expressed genes associated with stress responses during bacterial conjugation due to precence of nano/microplastics in the environment

**Analysis Workflow**
**Step 1 — Data Retrieval from GEO**
Access the GEO database.
Locate the dataset GSE248909.
Open the GEO2R analysis interface.
Assign samples to appropriate experimental groups.
Run GEO2R using the limma statistical framework.
Download the processed gene expression table.

**The downloaded dataset contains:**
Gene_ID
Gene_Name
COG
Expression values for multiple samples (log2FC)

**Step 2 — Data Processing in R**
The dataset is imported into R/RStudio, where preprocessing steps include:
removing metadata columns from the numeric matrix
converting expression values to numeric format
cleaning column names
setting Gene_ID as row identifiers
This ensures compatibility with downstream analysis tools.

**Step 3 — Exploratory Data Analysis**
To evaluate the overall structure of the dataset, several exploratory visualizations are generated.
**1. Expression Distribution (Boxplot)**
This plot shows the distribution of log2 fold-change values across samples.
_It is useful for detecting:_
sample variability
potential outliers
normalization consistency

**2. Density Plot**
Density curves illustrate the global expression distribution of each sample.
Overlapping curves suggest similar transcriptomic distributions, while deviations may indicate treatment effects.

**3. Principal Component Analysis (PCA)**
PCA is used to reduce the high-dimensional gene expression dataset into a low-dimensional representation.
This allows visualization of global transcriptomic similarity between samples.

**4. Differential Expression Analysis**
To identify genes with significant transcriptional changes, the following metrics are calculated:
mean log2 fold change
gene-wise variability
pseudo p-values derived from expression variance

_Genes are classified as:_
Upregulated
Downregulated
Not Significant (NS)

_based on thresholds:_
|log2FC| > 1
p-value < 0.05

**5. Visualization of Differential Expression (Volcano Plot)**
The volcano plot integrates magnitude of expression change (log2FC) with statistical significance (-log10 p-value).
_This visualization highlights genes that are:_
strongly upregulated
strongly downregulated

These genes represent potential functional regulators of stress response pathways.

**6. Heatmap of Top 50 Differentially Expressed Genes**
A heatmap is generated for the 50 genes with the largest absolute log2FC values.

This visualization reveals:

clustering of samples
coordinated gene expression patterns
transcriptional signatures associated with specific treatments

_From the DEG analysis, the top 10 most strongly upregulated and downregulated genes are extracted._

The resulting dataset includes:

Gene_ID
Gene_Name
COG functional category
log2 Fold Change
p-value
regulation status

These genes represent candidate transcriptomic biomarkers associated with PLASTIC-stress responses.

**Output Files**
Figures
Boxplot_expression_distribution
Density_plot_expression
PCA_transcriptomic_clustering
Volcano_plot_DEG
Heatmap_top50_genes
Tables
Top10_DEGs.csv
Top10_DEGs.xlsx

(These files can be used for further functional enrichment or pathway analysis)

**Tools and Software**
GEO / GEO2R	Dataset retrieval and preprocessing
R / RStudio	Statistical analysis and visualization
ggplot2	Data visualization
pheatmap	Heatmap generation
dplyr / tidyr	Data manipulation

Understanding transcriptional responses in E. coli during conjugation-related stress provides insights into how bacterial cells adapt to oxidative and environmental pressures, especially to the presence of plastic contamination

The identified genes may serve as potential biomarkers for monitoring bacterial stress responses or conjugation activity, which could be relevant in studies of **Targeted metagenomics with biomarkers**

