

# SKILLS 

Q1: Do you know the basics of working in bash with the unix commandline? Can you change directory, move between locations, copy/modify files, and work with scripts? 
Y: You're good to proceed (Go to Q2) 
N: You should start by getting familiar with the unix commandline (ie working from the terminal), in order to understand how best to install and run riboviz. We recommend the online Software Carpentries for the Unix Shell beginner-friendly resources [here](https://swcarpentry.github.io/shell-novice/) which can be worked through at your own pace, and should give you the information you need to confidently use the terminal and operate riboviz. 

Q2: Do you know how to use git version control? Can you clone a repository, switch between branches and pull the latest changes from a remote repository?
Y: You're good to proceed (Go to Q3)
N: It's worth spending the time to learn at least these basics of version control, as riboviz and the example-datasets repository contain various versions of files, and will be updated in future. Learning git version control will help you get set up correctly, and run the version of riboviz and example-datasets you need. To find out more, work through the Software Carpentries' ['Version Control with Git' workshop materials](https://swcarpentry.github.io/git-novice/). 

Q3: Will you be running riboviz locally (on your own computer or laptop) or on a cluster computer? 
Locally: You're good to proceed (Go to Q??)
Cluster Computing: (Go to Q4)

Q4: Is this the University of Edinburgh Eddie Compute Cluster? 
Y: Check our documentation on running riboviz on Eddie at the riboviz ["Running the riboviz workflow on Eddie" in `docs/user/run-on-eddie.md`](https://github.com/riboviz/riboviz/blob/develop/docs/user/run-on-eddie.md). (Go to Q5)
N: We don't have very many resources on how to run on other computing clusters, but it might be worth checking how it's done on the Eddie compute cluster (["Running the riboviz workflow on Eddie" in `docs/user/run-on-eddie.md`](https://github.com/riboviz/riboviz/blob/develop/docs/user/run-on-eddie.md)), and also looking into our containerised riboviz ([riboviz containers repository](https://github.com/riboviz/containers)) to help the install process.  Premal Shah's lab has got riboviz running on their Rutgers cluster, and might also have advice. (Go to Q??)

Q5: Are you familiar with the Eddie compute cluster? 
Y: You're ready to proceed (Go to Q6)
N: The Eddie team have put together some documentation and an ['Introduction to Eddie' course](https://www.wiki.ed.ac.uk/display/ResearchServices/Introduction+to+Eddie) you can work through to familiarise yourself with the Eddie system. It will requite your unix shell skills, and a university login to access. (Go to Q??)



# INSTALLING RIBOVIZ 

Q14: Will you be installing riboviz locally (on your own computer or laptop) or on a cluster computer? 
Locally: You're good to proceed (Go to Q16)
Cluster Computing: (Go to Q15)

Q15: Is this the University of Edinburgh Eddie Compute Cluster? 
Y: Riboviz is able to run on the Eddie compute cluster, and has been set up to do so for those with access to the `wallace_rna` Wallace lab group drive.  For access to this drive, contact Edward Wallace. Check and follow our documentation on running riboviz on Eddie at the riboviz ["Running the riboviz workflow on Eddie" in `docs/user/run-on-eddie.md`](https://github.com/riboviz/riboviz/blob/develop/docs/user/run-on-eddie.md). If you have acccess to the `wallace_rna` space, create a new folder within that lab drive space, and clone riboviz (and example-datasets if required) into it as detailed within [the riboviz Eddie documentation](https://github.com/riboviz/riboviz/blob/main/docs/user/run-on-eddie.md#get-riboviz-and-example-datasets). (Go to Q??)
N: As previously mentioned, we don't have very many resources on how to install & run on other computing clusters, but it might be worth checking how it's done on the Eddie compute cluster (["Running the riboviz workflow on Eddie" in `docs/user/run-on-eddie.md`](https://github.com/riboviz/riboviz/blob/develop/docs/user/run-on-eddie.md)), and also looking into our containerised riboviz ([riboviz containers repository](https://github.com/riboviz/containers)) to help the install process.  Premal Shah's lab has got riboviz running on their Rutgers cluster, and might also have advice. 

Q16: Have you followed the ["Install RiboViz and dependencies"](https://github.com/riboviz/riboviz/blob/main/docs/user/install.md) instructions?
Y: You're ready to run the riboviz vignette (a small subsampled test dataset)! (Go to Q17)
N: Go ahead and work through the [installation instructions](https://github.com/riboviz/riboviz/blob/main/docs/user/install.md)

Q17: Does the standard vignette run successfully, and produce output 


# DATASET 

Q6: Do you have the raw data on your system as `.fastq` files? 
Y: You're good to proceed. (Go to Q7)
N: If they're publicly available, you can download them using tools such as the `fasterq-dump` utility from SRA Toolkit. We have details on [how to use this tool on Eddie](https://github.com/riboviz/riboviz/blob/main/docs/user/run-on-eddie.md#download-fastq-data-files-from-the-short-read-archive-sra-initial-setup), but if you're working locally, you may have to find system-specific details. 

Q7: Do you know the adapters for the dataset samples? 
Y: Keep these handy, as you'll need to include this in the configuration yaml file for the `adapters` parameter - see more details in the riboviz documentation: ["Configuring the Riboviz Workflow"](https://github.com/riboviz/riboviz/blob/main/docs/user/prep-riboviz-config.md#configuration-parameters). (Go to Q8)
N: If this is a publicly available dataset, check the paper's methods section and supplemental information, and follow some of the troubleshooting steps listed in ["How to Set Up A New Dataset"](https://github.com/riboviz/example-datasets/blob/main/add-new-dataset.md)

Q8: Does your dataset include barcodes? 
Y: If you did the library prep, you'll know this. Otherwise, read the paper's methods section and supplementary information. Once you know that it does include these, firstirst, read our documentation on ["Run UMI extraction, deduplication and demultiplexing examples"](https://github.com/riboviz/riboviz/blob/main/docs/user/run-dedup-demultiplex-examples.md), paying attention to barcode-specific config parameters `multiplex_fq_files` and `sample_sheet`.  We provide small simulated test 'vignettes' for data with barcodes, and it's worth running this as described in that documentation before attempting a full-size dataset run. You will need to generate a specific 'sample sheet' `.tsv` file with specific columns (find more details on sample sheets in the ["Configuring the Riboviz Workflow" documentation](https://github.com/riboviz/riboviz/blob/main/docs/user/prep-riboviz-config.md#sample-sheet). Example-datasets contains an example of a dataset with barcodes listed in a sample sheet: [Gupta et al. 2018](https://github.com/riboviz/example-datasets/blob/main/fungi/saccharomyces/Gupta_2018_tRNA_Modification_Carbon_Nitrogen_Metabolism_RPF_9-samples_barcodes.tsv). You need to list each sample ID and the barcode for that sample in this sample sheet file, with the sample IDs matching those listed in your configuration yaml file. 
N: You're good to proceed. (Go to Q9)

Q9: Does your dataset include UMIs? 
Y: If you did the library prep, you'll know this. Otherwise, read the paper's methods section and supplementary information. Once you know that it does include these, first read our documentation on ["Run UMI extraction, deduplication and demultiplexing examples"](https://github.com/riboviz/riboviz/blob/main/docs/user/run-dedup-demultiplex-examples.md), paying attention to UMI-specific config parameters `dedup_stats`, `dedup_umis`, `extract_umis`, `group_umis` and `umi_regexp`.  We provide small simulated test 'vignettes' for data with UMIs, and it's worth running this as described in that documentation before attempting a full-size dataset run.
N: You're good to proceed. (Go to Q10)

Q10: Is the organism already in the [example-datasets](https://github.com/riboviz/example-datasets) repository? Go to the kingdom folders & check whether that species already has files.
Y: Clone the repository to the computer system you'll be working from (e.g. local or cluster) (Go to Q11)
N: If there are any similar organisms (e.g. within the same kingdom, or a species from the same genus), it might still be worth running one of those taxa through riboviz and considering whether those can be adapted or used as a rough template for your own organism of interest. Also, be sure to check out [the example-datasets guide to setting up a new dataset](https://github.com/riboviz/example-datasets/blob/main/add-new-dataset.md) as this gives step-by-step details on how to proceed. You can even choose to submit a new dataset to the example-datasets repository by submitting a Pull Request.


Q11: Do you have corresponding transcript-centric annotation files in FASTA and GFF format? 
Y: You're good to proceed. (Go to Q12)
N: There are instructions on how to go about generating transcript-centric annotation files in the documentation in example-datasets repo on [How to set up a new dataset](https://github.com/riboviz/example-datasets/blob/main/add-new-dataset.md#setting-up-a-new-species), including details on a script in the `create_riboviz_style_cds_gff_acope3-278` branch of riboviz. For more information on this, you can also check the discussions on riboviz issue ticket [#278 - Creating riboviz-friendly fasta and gff files](https://github.com/riboviz/riboviz/issues/278). Feel free to add comments to this ticket, or to create a new riboviz issue ticket, if you have questions about this process. 

Q12: Are your annotation FASTA and GFF files riboviz-friendly? Have you followed ["Check FASTA and GFF files for coding sequence (CDS) features"](https://github.com/riboviz/riboviz/blob/main/docs/user/check-fasta-gff.md) and run the riboviz tool `check_fasta_gff` to check? 
Y: Running `check_fasta_gff` reports very few issues, ie. only tens, of which most can be traced back to biologically-interesting quirks with some googling and investigation of those genes. You're good to proceed (Go to Q13)
N: Run `check_fasta_gff`, and check the issue summary.  If there are a lot of issues, consider the quality of your transcriptome files.  If roughly half of the reads show issues relating to missing start or stop codons, this might indicate issues with 'strandedness'.  Riboviz only accepts files showing coding sequences on the positive/forward strand. It might be necessary to generate your annotation files if existing files seem to throw up lots of issues when run through this tool. There are instructions on how to go about this (as well as more details on what riboviz expects from annotation files) in the documentation in example-datasets repo on [How to set up a new dataset](https://github.com/riboviz/example-datasets/blob/main/add-new-dataset.md#setting-up-a-new-species), including details on a script in the `create_riboviz_style_cds_gff_acope3-278` branch of riboviz. For more information on this, you can also check the discussions on riboviz issue ticket [#278 - Creating riboviz-friendly fasta and gff files](https://github.com/riboviz/riboviz/issues/278). Feel free to add comments to this ticket, or to create a new riboviz issue ticket, if you have questions about this process. 











# RUNNING RIBOVIZ


https://github.com/riboviz/riboviz/blob/main/docs/user/run-vignette.md
