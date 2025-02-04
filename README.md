# 1KSA-Genome-Assembly-Pipeline-Nextflow
This repository contains a nextflow pipeline for denovo genome assembly of long ONT reads.
This pipeline was built to support the genome assembly and analysis of the 1KSA project - A pilot project aimed at sequencing and assembling indigenous South African species. Detailed step by step instructions on how to run this pipeline on the CHPC can be found under files, labelled Instructions.txt.

# Introduction

This workflow uses the following tools:
* Dorado for basecalling
* Samtools for converting bam files to fastq files
* Nanoplot for quality check
* Nanofilt for filtering and trimming
* Flye for genome assembly
* Racon for first round assembly polishing
* Medaka for second round assembly polishing
* BUSCO for assembly quality assessment
* QUAST for assembly quality assessment
* KMC for counting of k-mers in DNA


![Image Alt text](97d92b1b-f47a-4e23-adcd-27b8d0f559cb.jpg)

If basecalling was done on the sequencing machine, the main2.nf script can be used to run genome assembly once the fastq files have been concatinated. 


# Dependencies

The following modules need to be loaded on the CHPC before running the pipeline:
* module purge
* module load chpc/BIOMODULES
* module load dorado
* module load samtools/1.9
* module load nanoplot
* module load nanofilt
* module load flye/2.9
* module load minimap2
* module load racon/1.5.0
* module load medaka/1.11.3
* module load quast/4.6.3
* module load quast/4.6.3
* module load busco/5.4.5
* module load bbmap/38.95
* module load metaeuk
* module load python
* module load R
* module load KMC
* module load nextflow/23.10.0-all

The following models and databases need to be downloaded before running the pipeline:
* Dorado: dorado download --model dna_r10.4.1_e8.2_400bps_hac@v4.2.0
* Busco: busco --download eukaryota_odb10


# Usage

To obtain the workflow, having installed nextflow, users can run:
* nextflow run main.nf --help
to see the options for the workflow.

# Workflow outputs

The primary outputs of the pipeline include:
* A fastq quality control report
* 3 assembled fasta files (From Flye, Racon and Medaka)
* A busco report
* A quast quality report
