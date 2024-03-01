## Quality Control and Trimming
We use the program fastqc to evaluate the quality of our reads. We will then trim reads using fastp. Finally, we will use fastqc to evaluate the efficacy of our trimming.

### FastQC of Raw Files
FastQC evaluates sequences data for a variety of common problems and helps point the user towards areas of concern for subsequent trimming.

Create and submit a FastQC job for each of your fastq or fastq.gz read files.
A generic fastqc job can be found here: [FastQC.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/fastqc.job).

Download your FastqQC results using Globus and open the .html files in your browser.

### Read Trimming with fastp
We trim our reads to remove poor quality basepairs and residual adapter sequence using fastp.

fastp does not require an illumina adapter to remove adapter sequences, but you can supply one for better adapter trimming, and we use one here. LAB uses two types of adapters, itru and nextera. Because we do not necessarily know which adapters have been used, I have included a fasta file that includes both, called `illumina_adapters.fas`. The job file currently points to a directory containing the adapter file. 

Based on the quality of your reads (as determined by fastQC), we may want to edit the parameters in  `fastp.job`. The job file contains descriptions and suggestions for each parameter. Note that the output parameter of the fastp job compresses the trimmed files, to save drive space. Note that the output parameter of the fastp job compresses the trimmed files, to save drive space.

Trimmed reads will be saved in `/data/trimmed_sequences`, so create this directory. 

Create and submit a fastp job for each of your fastq or fastq.gz read files.
A generic fastqc job can be found here: [fastp.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/fastp.job). 


## FASTQC TRIMMED READS 
We next run fastQC on all our trimmed reads to check our trimming parameters. We will run the same job file we ran the first time, just using different target files.

### Run FastQC
Create and submit a FastQC job for each of your trimmed fastq.gz read files.
A generic fastqc job can be found here: [FastQC.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/fastqc.job).

Download your FastqQC results using Globus and open the .html files in your browser.
