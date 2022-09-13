---
fig-cap-location: top
from: markdown+emoji
---

# **Run the nf-core/rnaseq pipeline on Pawsey’s Nimbus VM instance**

<div class="questions">

### **Questions**

- What does the actual nf-core/rnaseq command look like?
- What are the main input parameters?
- What are the outputs?
- What are the output log files?

</div>  

<div class="objectives">

### **Objectives**
- Understand and excecute the nf-core/rnaseq command
</div>  


### **Run the pipeline on Pawsey-Nimbus VM instance**

- Please go back to the command-line(Terminal) window on which you have logged on to the Nimbus training instance.
- In case the window has been closed accidently or if you have been logged-off, you will need to follow the log-in steps on the `Setup` page.

Check your path by typing:
```r
pwd
```
- You should be in the path: `/home/training/base_directory/working_directory` 
- If you are not, move into the above path by typing:
```r
cd /home/training/base_directory/working_directory
```

#### **Excecuting the Nextflow nf-core/rnaseq pipeline**
We will run the single nf-core/rnaseq command using a utility called __screen__ in unix.

What is the `screen` command?

- The __screen command__ in Linux provides the ability to launch and use multiple shell sessions from a single ssh session. 
- When a process is started with ‘screen’, the process can be detached from session & then can reattach the session at a later time. 
- When the session is detached, the process that was originally started from the screen is still running and managed by the screen itself. 
- The process can then re-attach the session at a later time, and the terminals are still there, the way it was left.
- In short, we can use a `single Terminal` and `multiple screen` sessions in the terminal to do multiple different things.
<br><br> **NOTE** If this sounds too complicated, the other alternative is to open a new `terminal` window :-) for a new task.


#### **(1) Start a new screen window**
`-S`: It will start a new window within the screen and also gives a name to the window. 
It creates a session which is identified by that name. The name can be used to reattach screen at a later stage.

```r
screen -S run_nextflow_in_screen
```

#### **(2) Run the nf-core/rnaseq command**
<font size="2.5">
```default

cvmfs_path=/cvmfs/data.biocommons.aarnet.edu.au/Final_resources_250722
  
nextflow run $cvmfs_path/nfcore_pipeline/rnaseq/ \                                    # the excecutable file
    --input samplesheet.csv \                                                         # samplesheet file-name
    -profile singularity \                                                            # profile e.g. singularity
    --fasta $cvmfs_path/Mouse_chr18_reference/chr18.fa \                              # Path: Genome fasta file
    --gtf $cvmfs_path/Mouse_chr18_reference/chr_18_startOfLine.gtf \                  # path: gtf file
    --star_index $cvmfs_path/Mouse_chr18_reference/chr18_STAR_singularity_index/ \    # path: 'STAR' index file
    --max_memory '6 GB' --max_cpus 2 \                                                # memory and cpu resources 
    --outdir results \
    -with-report excecution_report.html \                                             # Excecution log file-name 
    -with-timeline timeline_report.html                                               # Timeline log file-name

```
</font>


- The [CernVM File System](https://cernvm.cern.ch/fs/) i.e. `cvmfs` provides a scalable, reliable and low-maintenance software distribution service.
- The names of cvmfs folders (e.g. __Final_resources_250722__) and files need to be standardised (make these more user-friendly). This is __work in progress__.


#### **(3) Detach from the above screen session**
`-d`: It is used to detach a screen session so that it can be reattached in future. 
It can also be done with the help of shortcut key ```Ctrl-a + d```

#### **(4) Reattach the screen-session to check the progress**
`-r` : It is used to reattach a screen session which was detached in past.
```r
screen -r run_nextflow_in_screen
```
Repeat Steps (3) and (4) to check the the excecution status of the command.

- The nf-core/rnaseq command will take about 18-22 minutes to run to completion.
- In the mean time we will proceed to discuss some of the important output and log files. 
- We plan to make a `pre-processed results folder` available for download. If one of more attendess have a problem excecuting the nf-core command, they will be able use these pre-computed results.   
- An `scp command` to transfer required files from the results folder on the VM instance to your local machine will also be made available.


<div class="challenge">

### **Challenge**
- Which parameters in the above `nf-core/rnaseq` command seem to be mandatory?
<br>**NOTE** This is a trick question , but a very important one :smirk:
  
<details>
<summary>Solution</summary>
- If we are working with model organisms such as human/mouse
    - The ONLY mandatory parameters which the user needs to supply to the pipeline are
        -   The samplesheet : `--input samplesheet.csv`
        -   The name of the genome version e.g. `--genome GRCh37`
        -   The profile '-profile'
    - So the most basic command (when a standard genome is available from a nf-core resource) is 

```default
nextflow run nf-core/rnaseq \
    --input samplesheet.csv \
    --outdir <OUTDIR> \
    --genome GRCh37 \
    -profile <docker/singularity/podman/shifter/charliecloud/conda/institute>
```
- Provided with a genome ID such as `--genome GRCh37`, the nf-core/rnaseq pipeline will download all requried genome-related files at run-time.
- However when we are working with our own non-model species of interest, we will need to provide the genome related index files.
- In this workshop, although we are working with a standard version of the mouse genome (GRCh38/mm10) , inorder to save time, bandwidth and hard-disk space on the individial VM instances, we have hosted the genome files in a central repository called [`Cern-VM-FS`](https://cernvm.cern.ch/fs/), and hence provided the cvmfs paths. 

</details>
</div>  




<div class="keypoints">

### **Key points**
- Pawsey Nimbus VM is a good resource to run nf-core piplelines
</div>  



  
