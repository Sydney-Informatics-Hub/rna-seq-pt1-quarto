---
fig-cap-location: top
---

# Introduction to nfcore-rnaseq

<div class="questions">

### Questions

- What is nfcore-rnaseq
</div>  

<div class="objectives">

### Objectives

- Introduction to the nfcore-rnaseq pipeline
</div>  


### nfcore-rnaseq

- nfcore-rnaseq is a bioinformatics pipeline that can be used to analyse RNA sequencing data obtained from organisms with a reference genome and annotation.
- The pipeline is built using [Nextflow](https://www.nextflow.io/)
-  It uses [Docker](https://www.docker.com/)/[Singularity](https://sylabs.io/) containers making installation trivial and results highly reproducible. 
-  Citation : doi: [10.5281/zenodo.1400710](https://doi.org/10.5281/zenodo.1400710)

### Workflow 

![A typical bioinformatics workflow ](/fig/bioinformatics_workflow.png)

- nfcore-rnaseq uses [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/),[MultiQC](http://multiqc.info/), [Trim Galore!](https://www.bioinformatics.babraham.ac.uk/projects/trim_galore/) and other tools for quality control and pre-processing of sequencing reads.
- The pipeline uses [STAR](https://github.com/alexdobin/STAR), [RSEM](https://github.com/deweylab/RSEM), [HISAT2](https://ccb.jhu.edu/software/hisat2/index.shtml) or [Salmon](https://combine-lab.github.io/salmon/) with gene/isoform counts for alignment and quantification.
- The pipeline uses [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html) for initial exploratory analysis of the generated raw-counts matrix.


### Platforms to run the pipeline
- **Local machine**: Is this sufficient?
- **High Performance Computing (HPC)**: USyd-Artemis, NCI-GADI, Amazon cloud ...
- **Nimbus Virtual machine (VM) instances** : Pawsey Supercomputing.  

In this workshop, we will be using training Nimbus Virtual machine (VM) instances provided by [Pawsey Supercomputing Center](https://pawsey.org.au/)






<div class="keypoints">

### Key points

- nfcore-rnaseq is an nextflow pipeline which works with containers such a sigularity and docker.
- nfcore-rnaseq is portable across platforms using easy to use configuration files.
</div>  
