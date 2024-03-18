## Read Assembly
There are multiple programs available for assembling your reads into longer continuous sequences. Some commonly used ones are [SPAdes](https://github.com/ablab/spades), [MitoFinder](https://github.com/RemiAllio/MitoFinder), [GetOrganelle](https://github.com/RemiAllio/MitoFinder), and [MitoZ](https://github.com/linzhi2013/MitoZ). We are going to focue on two programs today: SPAdes and GetOrganelle.

### SPAdes 
We are going to run SPAdes on all our trimmed paired and unpaired reads. 

We need a SPAdes results folder for SPAdes: `data/results/spades/SRRxxxx`. The SPAdes results for each paired set of reads (each hydra job) will be saved in a sample-specific directory within this directory. You need to make The contig file that will be used in the next annotation step is named with a generic contig.fasta. I often change the name of the contig file to include the sample name (e.g. `cp contig.fasta > SRRxxxx.contig.fasta`).

Create and submit a SPAdes job for each set of trimmed fastq or fastq.gz read files.
A generic SPAdes job can be found here: [SPAdes.job](https://raw.githubusercontent.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/main/job_files/spades.job). 

**Don't forget that you will need to create `data/results/spades/SRRxxxx` first.**

### GetOrganelle
We are also going to run GetOrganelle on all our trimmed paired and unpaired reads.

We need a results folder for GetOrganelle: `data/results/getorganelle/SRRxxxx`. The GetOrganelle results for each paired set of reads (each hydra job) will be saved in a sample-specific directory. Unlike SPAdes, GetOrganelle creates that directory, so you don't need to create that (and GetOrganelle will stop and give you and error if you do create it). The contig file(s) that will be used in the next annotation step are named similar to either animal_mt.Kxxx.complete.graph1.x.path_sequence.fasta if GetOrgenelle found a complete mitogenome, or animal_mt.Kxxx.scaffolds.graph1.x.path_sequence.fasta if it found contigs that could not be circularized. 

Create and submit a GetOrganelle job for each set of trimmed fastq or fastq.gz read files.
A generic GetOrganelle job can be found here: [GetOrganelle.job](https://raw.githubusercontent.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/main/job_files/getorganelle.job).

**Don't forget that you will need to create `data/results/getorganelle` first.**
