## SRA Data
Before we start genome skimming, we need read data to analyze. We have chosen some Sequence Read Archive (SRA) data that we have tested for you to run your analyses on. 

>The SRA is NIH's archive of high-throughput sequencing data and is part of the International Nucleotide Sequence Database Collaboration (INSDC) that includes the NCBI Sequence Read Archive (SRA), the European Bioinformatics Institute (EBI), and the DNA Database of Japan (DDBJ). Data submitted to any of the three organizations are shared among them.

https://www.ncbi.nlm.nih.gov/sra

We have assigned SRAs for you to analyze. Lets learn a little more about the sample. Go the the NCBI SRA website above and search for your SRAs. Make sure to note the phylum of your reads, you will need this later.

We download SRA data from the NCBI website using the prefetch program in SRA toolkit, which is already installed as a module in `bioinformatics/` on hydra. 

>The SRA toolkit is a set of compiled binaries and corresponding source code for tools that download, manipulate and validate next-generation sequencing data stored in the NCBI SRA archive.

Load the SRA toolkit module.

```
module load bioinformatics/sratoolkit
```
To download SRAs, you can either submit a separate prefetch command for each of your files, or you can create a text files containing a list of SRA accession numbers and download them all using a single prefetch command. Run prefetch from `data/sra/`. Everything else will be run from `jobs/`.

Download your SRA files.
```
prefetch SRRxxxx
```
or

```
prefetch --option-file SraAccList.csv
```

Whoops, this most likely didn't work for you if you havenpt used SRA toolkit before, giving an error something like:

"This sra toolkit installation has not been configured.  
Before continuing, please run: vdb-config --interactive"

So, lets do that
```
vdb-config --interactive
```

<img src="https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/images/vdb-config.png" alt="vdb-config" width=600px>


Try downloading your SRA files again

```
prefetch SRRxxxx
```

You can also check the integrity of the requested SRA data using vdb-validate

```
vdb-validate SRRxxxx
```
**I would recommend having this SRA accession number handy on your laptop, because you will be using it a lot, so having the ability to quickly copy it anytime is very useful.**

Prefetch downloads files in SRA format (ending in .sra). These need to be converted to fastq files. For this, we use another program from sratoolkit called fasterq-dump. We run this in a job, which can be found here:
[fasterq-dump](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/raw/main/job_files/fasterq_dump.job)

Fasterq-dump converts SRA data to fastq data, which can often be very large. Typically, we would subsequently compress fastq files to fastq.gz files, using gzip. However, this can take a long time, over an hour for some of the files here. Luckily, we do not need fastq.gz read files, our programs can analyze fastq data. 

Submit fasterq-dump job files for each of your SRAs in `data/sra/`, using `data/raw` as your output directory.  
**Don't forget that you will need to create `data/raw` first.**
