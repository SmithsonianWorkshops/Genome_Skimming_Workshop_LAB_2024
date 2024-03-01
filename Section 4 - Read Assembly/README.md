## Read Assembly
### SPAdes 
We are going to run SPAdes on all our trimmed paired and unpaired reads. SPAdes error-corrects all reads, then performs a de-novo assembly using both pair-end and single-end reads and outputs a set of contigs. 

### Run SPAdes 
Create and submit a SPAdes job for each of your trimmed fastq or fastq.gz read files.
A generic SPAdes job can be found here: [SPAdes.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/spades.job). 

The SPAdes results for each paired set of reads will be saved in a sample-specific directory: `/data/results/spades/SAMPLE`. The contig file that will be used in the next annotation step is names with a generic contig.fasta

Run the SPAdes shell script, including the path to the directory containing your trimmed read files. For most, it should be something like: `/scratch/genomics/<USERNAME>/<PROJECT>/data/trimmed_sequences`. 
```
sh spades.sh <path_to_trimmed_sequences>
```

Your results should be in `/scratch/genomics/<USERNAME>/<PROJECT>/data/results/spades`. The results for each sample will be in a separate folder, named with the sample name. 

