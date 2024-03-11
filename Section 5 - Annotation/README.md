## Annotation of MitoGenomes
There are multiple programs for annotation of mitochondrial genomes, including [MitoFinder](https://github.com/RemiAllio/MitoFinder), [MITOS](https://gitlab.com/Bernt/MITOS), and [MitoZ](https://github.com/linzhi2013/MitoZ). We will focus annotation using MitoFinder, but will also look at improving incomplete annotations using MITOS.

### MitoFinder
Mitofinder can perform a de-novo assembly of reads into contigs which it can then annotate, but it can also annotate external assembled contigs, which is what we will do here. We will run MitoFinder twice, once using the resultant contigs from the SPAdes assembly and once using the contigs from the GetOrganelle assembly. 

MitoFinder requires a mitochondrial genome database in GenBank (.gb) format.  It is relatively easy to generate your own reference database (see [getting reference genomes from NCBI](https://github.com/RemiAllio/MitoFinder?tab=readme-ov-file#how-to-get-reference-mitochondrial-genomes-from-ncbi) on the MitoFinder github page). You can use a general Metazoa reference database for all your assemblies, regardless of taxa, or you can create a taxa-specific database. One disadvantage to the Metazoan database is time, annotations using a large reference database can take several hours compared to much less than an hour using a smaller database.  

We have multiple phyla-specific reference databases available for usage, as well as a larger Metazoan database.

We need a results folder for Mitofinder: `data/results/mitofinder`. Within this directory will be a job-specific directory for each submitted job annotated. Within each of these will be a "SAMPLE_Final_Results" folder, which will contain the mitogenome annotations for that contig.

We are going to annotate both the SPAdes results and the GetOrganelle results with MitoFinder.

Create and submit a MitoFinder job for your contig files, from both your SPAdes and GetOrganelle assemblies. A generic MitoFinder job can be found here: [MitoFinder.job](https://raw.githubusercontent.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/main/job_files/mitofinder.job). You will need to change multiple fields in your MitoFinder jobs. Not only must you change the path to the contig file, but you must also set the genetic code (`-o`) and the reference database (`-r`). See the bottom of the supplied job file for how to set these two parameters.

**Don't forget that you will need to create `data/results/mitofinder` first.**

### MITOS
MitoFinder does not always do a great job of annotating all the features present in your assembly, especially when there are not closely related taxa in the reference library. In these instances, MITOS can sometimes annotate genes that MitoFinder was not able to find. However, even with good references, MITOS can sometimes find some features, such as tRNA's and rRNA's, that MitoFinder does not. We will use the GetOrganelle contig file as our input mitogenome for MITOS.  

MITOS requires a reference database. The developers have supplied one for our usage, and while it is possible to make your own, it is not nearly as simple as it is in MitoFinder, so we will use the available one.


Create and submit a MITOS job for your GetOrganelle contig file. A generic MITOS job can be found here: [MITOS.job](https://raw.githubusercontent.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/main/job_files/mitos.job). In addition to your input and output paths, you will also need to change the genetic code (-c) used before submitting the job.  
**Don't forget that you will need to create `data/results/mitos` first.**

