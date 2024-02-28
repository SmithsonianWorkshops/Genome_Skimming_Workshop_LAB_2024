## SRA Data
Before we start genome skimming, we need read data to analyze. We have chosen some Sequence Read Archive (SRA) data that we have tested for you to run your analyses on. 

>"The SRA is NIH's archive of high-throughput sequencing data and is part of the International Nucleotide Sequence Database Collaboration (INSDC) that includes the NCBI Sequence Read Archive (SRA), the European Bioinformatics Institute (EBI), and the DNA Database of Japan (DDBJ). Data submitted to any of the three organizations are shared among them."

https://www.ncbi.nlm.nih.gov/sra

We download SRA data from the NCBI website using the program SRA toolkit. This program is already installed on hydra.

Load the sratoolkit module.

```
module load bioinformatics/sratoolkit
```

Download SRA files using the list of SRA accession numbers that you created earlier.

```
prefetch --option-file SraAccList.csv
```

Whoops, this most likely didn't work for you, giving an error something like:

"This sra toolkit installation has not been configured.  
Before continuing, please run: vdb-config --interactive"

So, lets do that
```
vdb-config --interactive
```

<img src="images/vdb-config interactive.png" width=300px alt="vdb-config interactive mode>


Try downloading your SRA files again

```
prefetch --option-file SraAccList.csv
```

Prefetch downloads files in SRA format (ending in .sra). These need to be converted to fastq files. For this, we use another program from sratoolkit called fasterq_dump. We run this in a job, which can be found here:
[fasterq_dump](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/fasterq_dump.job)

Fasterq_dump converts SRA data to fastq data, which can often be very large. Typically, we would subsequently compress fastq files to fastq.gz files, using gzip, as such:
```
gzip path_to_fastq_file/SAMPLE.fastq
``````
However, this can take a long time, up to an hour for some of the files here. Luckily, we can use fastq data with our initial programs.