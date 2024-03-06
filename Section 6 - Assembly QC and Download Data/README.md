## Assembly QC and Downloading Data

### Assembly QC
We are going to use QUAST (QUality ASsessment Tool) to evaluate the quality of our assemblies. We are going to run QUAST on our SPAdes contigs

We need a QUAST results folder for QUAST: data/results/spades/. The QUAST results for each paired set of reads (each hydra job) will be saved in a sample-specific directory within this directory. You need to make The contig file that will be used in the next annotation step is named with a generic contig.fasta. I often change the name of the contig file to include the sample name (e.g. cp contig.fasta > SRRxxxx.contig.fasta).

Create and submit a QUAST job for your SPAdes contigs.fasta files, and for your "complete" mitogenome assembly from GetOrganelle. A generic QUAST job can be found here: [quast.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/quast.job).

**Don't forget that you will need to create data/results/quast first.**


### Map Reads to Reference
We are also going to map our trimmed reads to our mitochondrial contigs using two programs, [BWA-mem2](https://github.com/bwa-mem2/bwa-mem2), and [Bowtie2](https://github.com/BenLangmead/bowtie2). However, neither program can read compressed sequence data, so first we need to decompress our .fastq.gz files into .fastq files. We do this with gzip.

```
gzip -d /scratch/genomics/USER/PROJECT/data/trimmed_sequences/SRRxxxx_R1_PE_trimmed.fastq.gz
gzip -d /scratch/genomics/USER/PROJECT/data/trimmed_sequences/SRRxxxx_R2_PE_trimmed.fastq.gz
```
Both programs create SAM files, saving them in a samples-specific directory `data/results/bowtie2/SRRxxxx` or `data/results/bwa/SRRxxxx`. Make these directories.

Create and submit both a BWA-mem2 and a Bowtie2 job for your "complete" mitogenome assembly from GetOrganelle. Generic job files can be found here: [bwa.job]() and [bowtie2.job]().

### Downloading Data from Hydra
We are going to download a significant amount of data for further analyses on our laptops.  Using FileZilla, download the following data:
1.  Mitofinder Final_Results folder
2.  GetOrganelle Results
3.  QUAST results
4.  BWA Results
5.  Bowtie2 Results