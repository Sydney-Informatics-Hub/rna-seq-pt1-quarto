---
fig-cap-location: top
---

# **Qualimao multiQC**


<div class="questions">

### **Questions**

- 
- 
- 
</div>  

<div class="objectives">

### **Objectives**

- Understand the timelines for multiple processes
- Estimate the resource requirements for multiple processes
- Analysing the technical requirements to run nf-core pipelines

</div>  

### Qualimap
 Qualimap explores the features of aligned reads in the context of the genomic region they map to, hence providing an overall view of the data quality (as an HTML file). Various quality metrics assessed by Qualimap include:

DNA or rRNA contamination
5’-3’ biases
Coverage biases

### Quality control: aggregating results with MultiQC
Throughout the workflow we have performed various steps of quality checks on our data. You will need to do this for every sample in your dataset, making sure these metrics are consistent across the samples for a given experiment. Outlier samples should be flagged for further investigation and potential removal.

Manually tracking these metrics and browsing through multiple HTML reports (FastQC, Qualimap) and log files (Salmon, STAR) for each samples is tedious and prone to errors. MultiQC is a tool which aggregates results from several tools and generates a single HTML report with plots to visualize and compare various QC metrics between the samples. Assessment of the QC metrics may result in the removal of samples before proceeding to the next step, if necessary.