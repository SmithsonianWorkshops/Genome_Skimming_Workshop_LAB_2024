## Assembly QC and Downloading Data

### Assembly QC
We are going to use QUAST (QUality ASsessment Tool) to evaluate the quality of our assemblies. We are going to run QUAST on our SPAdes contigs

We need a QUAST results folder for QUAST: data/results/spades/. The QUAST results for each paired set of reads (each hydra job) will be saved in a sample-specific directory within this directory. You need to make The contig file that will be used in the next annotation step is named with a generic contig.fasta. I often change the name of the contig file to include the sample name (e.g. cp contig.fasta > SRRxxxx.contig.fasta).

Create and submit a QUAST job for your SPAdes contigs.fasta files, and for your "complete" mitogenome assembly from GetOrganelle. A generic QUAST job can be found here: [quast.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/quast.job).

**Don't forget that you will need to create `data/results/quast/SRRxxxx` first.**


### Map Reads to Reference
We are also going to map our trimmed reads to our getorganelle mitochondrial contigs using the program [Bowtie2](https://github.com/BenLangmead/bowtie2). 

Bowtie2 normally creates a SAM file, saving it in a samples-specific directory `data/results/bowtie2/SRRxxxx`. Make this directory. However, we want a BAM file (a binary version of a SAM file that usually are smaller and more efficient) that also does not contain any unassembled reads, so we are modifying our bowtie2 output using samtools, so the results of this process is a BAM file that only contains information for the reads that assembled to your mitochondrial reference. The samtools command is part of your bowtie2 job file, so you don't have to take any additional actions.

Create and submit a Bowtie2 job for your "complete" mitogenome assembly from GetOrganelle. A generic job files can be found here: [bowtie2.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/bowtie2.job).

**Don't forget that you will need to create `data/results/bowtie2/SRRxxxx` first.**

### Downloading Data from Hydra
We have finished analyzing our sample data in Hydra, so now we are going to download some data for further analyses on our laptops. First, make a directory for each sample, labeled SRRxxxx.  Using FileZilla, download the following data for each sample into it's respective folder:
1.  Mitofinder Final_Results folders
2.  GetOrganelle _Sequence.fasta
3.  QUAST results folders
5.  Bowtie2 .bam file