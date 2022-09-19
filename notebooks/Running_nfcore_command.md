---
fig-cap-location: top
from: markdown+emoji
---

# **Run the nf-core/rnaseq pipeline on Pawsey’s Nimbus VM instance**
  

<div class="objectives">

### **Objectives**
Run the nextflow command and relax :grinning:
</div>  


<div class="questions">

### **Questions**
How to run the nextflow command in terminal?
</div>

### **Run the pipeline on Pawsey-Nimbus VM instance**

::: {.callout-note appearance="simple"}

#### Why run the command now?
We need to allow ~20 mins for the command to run on the test data. For this reason we will run the command first. We will then discuss each step of this pipeline once it has completed. 

:::

#### **Excecuting the Nextflow nf-core/rnaseq pipeline**
On your terminal window, check your path by:
```default
pwd
```
You should be in the path: `/home/training/base_directory/working_directory`. If you are not, move into the above path by:
```default
cd /home/training/base_directory/working_directory
```

#### **Run the nf-core/rnaseq command**
<font size="2.5">
```default

cvmfs_path=/cvmfs/data.biocommons.aarnet.edu.au/Final_resources_250722

nextflow run $cvmfs_path/nfcore_pipeline/rnaseq/ \
                --input samplesheet.csv \
                -profile singularity \
                --fasta $cvmfs_path/Mouse_chr18_reference/chr18.fa \
                --gtf $cvmfs_path/Mouse_chr18_reference/chr_18_startOfLine.gtf \
                --star_index $cvmfs_path/Mouse_chr18_reference/chr18_STAR_singularity_index/ \
                --max_memory '6 GB' --max_cpus 2 \
                --outdir results \
                -with-report excecution_report.html \
                -with-timeline timeline_report.html

```
</font>

- The [CernVM File System](https://cernvm.cern.ch/fs/) i.e. `cvmfs` provides a scalable, reliable and low-maintenance software distribution service.
- The names of cvmfs folders (e.g. __Final_resources_250722__) and files need to be standardised (make these more user-friendly). This is __work in progress__.


- The process will run in the terminal and display updated real-time excecution status.
- The nf-core/rnaseq command will take about 18-22 minutes to run to completion.
- In the mean time we will proceed to discuss some of the important output and log files. 
- We plan to make a `pre-processed results folder` available for download. If one of more attendess have a problem excecuting the nf-core command, they will be able use these pre-computed results.   
- An `scp command` to transfer required files from the results folder on the VM instance to your local machine will also be made available.


<div class="challenge">

### **Challenge**
 
  
<details>
<summary>Solution</summary>

</details>
</div>  


::: {.callout-note appearance="simple"}

# Using 'screen' utility for advance command-line users 
We can run the single nf-core/rnaseq command using a utility called __screen__ in unix.

What is the `screen` command?<br>
The __screen command__ in Linux provides the ability to launch and use multiple shell sessions from a single ssh session. 

The following screen paramters are useful:<br>
`-S`: Start a new window within the screen and also gives a name to the window. 
It creates a session which is identified by that name. The name can be used to reattach screen at a later stage.

```r
screen -S run_nextflow_in_screen
```

`-d`: Used to detach a screen session so that it can be reattached in future. 
It can also be done with the help of shortcut key ```Ctrl-a + d```


`-r` : It is used to reattach a screen session which was detached in past.
```r
screen -r run_nextflow_in_screen
```
:::








<div class="keypoints">

### **Key points**
- Pawsey Nimbus VM is a good resource to run nf-core piplelines
</div>  



  
