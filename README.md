ITS2 eDNA Analysis Pipeline

This repository contains a comprehensive pipeline for processing ITS2 sequences from nematoda and platyhelminthes, classifying them using both Qiime2 and Kraken2/Bracken, and performing downstream decontamination and diversity analyses in R with Phyloseq.

Note: The pipeline is designed to be executed primarily on an Ubuntu system with access to the WSL or a Linux cluster environment.

Overview
The pipeline is divided into four main steps:

Conda Environment Set-Up & Database Preparation

Create and activate a dedicated Conda environment (bioenv) with required bioinformatics tools (e.g., entrez-direct, blast, taxonkit, kraken2, bracken).
Download and merge ITS2 sequences for nematoda and platyhelminthes from the NCBI nucleotide database.
Extract accession IDs, convert them to taxonomic IDs, and use TaxonKit to retrieve full taxonomy lineages.
Format the resulting files for Qiime2 classifier training.
QIIME2 Processing

Import demultiplexed paired-end reads and generate summary visualizations.
Use DADA2 for denoising and ASV (Amplicon Sequence Variant) generation.
Import reference sequences and taxonomy to train a custom Naïve Bayes classifier.
Classify representative sequences and create taxonomy barplots.
(Manual steps are needed for formatting and further processing in Excel/Qiime View.)
Kraken2 & Bracken Classification

Set up the Kraken2 database using the merged ITS2 sequences.
Classify the reads with Kraken2 and estimate abundances using Bracken.
Generate Krona plots and prepare reports for further visualization (e.g., using Pavian).
Phyloseq Analysis & Decontamination

Convert Qiime2 outputs into OTU/ASV tables suitable for R.
Use the decontam package to identify and remove contaminants.
Perform alpha and beta diversity analyses, create PCoA plots, and generate stacked bar plots with Phyloseq.
(Some steps require manual intervention for metadata curation and Excel-based formatting.)
Requirements
Operating System: Ubuntu (or similar Linux environment)
Conda: To manage environments and package installations
Software Packages:
QIIME2
Kraken2
Bracken
TaxonKit
DADA2 (within Qiime2)
R packages: phyloseq, decontam, ggplot2, vegan, etc.
Usage
Set-Up Environment:

Open Ubuntu (or your Linux terminal) and execute the provided commands to create and activate the bioenv conda environment.
Follow the instructions in the script to create a working directory and download ITS2 sequences.
Database and Reference Preparation:

Execute the sequence download, merging, and taxonomy formatting commands.
Follow the manual steps as noted (e.g., formatting taxonomy tables in Excel).
Run Qiime2 Analysis:

Transfer fastq files and metadata to the designated directory on your cluster.
Use the provided SLURM script (for example, qiime2_pipeline.sh) to submit your job.
Review output visualizations (e.g., demultiplexing summary, feature table, taxonomy classifications).
Kraken2 & Bracken Analysis:

Set up the Kraken2 database and run classification commands.
Generate reports and Krona plots for interactive visualization.
Phyloseq & Decontamination Analysis in R:

Convert Qiime2 outputs into the correct format and run the provided R scripts for decontamination and diversity analyses.
Customize the R scripts as needed based on your metadata and experimental design.
