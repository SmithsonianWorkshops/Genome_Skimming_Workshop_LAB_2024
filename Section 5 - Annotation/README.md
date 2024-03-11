## Annotation of MitoGenomes
There are multiple programs for annotation of mitochondrial genomes, including [MitoFinder](https://github.com/RemiAllio/MitoFinder), [MITOS](https://gitlab.com/Bernt/MITOS), and [MitoZ](https://github.com/linzhi2013/MitoZ). We will focus annotation using MitoFinder, but will also look at improving incomplete annotations using MITOS.

### MitoFinder
Mitofinder can perform a de-novo assembly of reads into contigs which it can then annotate, but it can also annotate external assembled contigs, which is what we will do here. We will run MitoFinder twice, once using the resultant contigs from the SPAdes assembly and once using the contigs from the GetOrganelle assembly. 

MitoFinder requires a mitochondrial genome database in GenBank (.gb) format.  It is relatively easy to generate your own reference database (see [getting reference genomes from NCBI](https://github.com/RemiAllio/MitoFinder?tab=readme-ov-file#how-to-get-reference-mitochondrial-genomes-from-ncbi) on the MitoFinder github page). You can use a general Metazoa reference database for all your assemblies, regardless of taxa, or you can create a taxa-specific database. One disadvantage to the Metazoan database is time, annotations using a large reference database can take several hours compared to much less than an hour using a smaller database.  

We have multiple phyla-specific reference databases available for usage, as well as a larger Metazoan database.

We need a results folder for Mitofinder: `data/results/mitofinder`. Within this directory will be a sample-specific directory for each contig annotated. Within each of these will be a "SAMPLE_Final_Results" folder, which will contain the mitogenome annotations for that contig.

We are going to annotate both the SPAdes results and the GetOrganelle results with MitoFinder.

Create and submit a MitoFinder job for your contig files, from both your SPAdes and GetOrganelle assemblies. A generic MitoFinder job can be found here: [MitoFinder.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/mitofinder.job). You will need to change multiple fields in your MitoFinder jobs. Not only must you change the path to the contig file, but you must also set the genetic code (`-o`) and the reference database (`-r`). See the bottom of the supplied job file for how to set these two parameters.

**Don't forget that you will need to create `data/results/mitofinder` first.**

### MITOS
MitoFinder does not always do a great job of annotating all the features present in your assembly, especially when there are not closely related taxa in the reference library. In these instances, MITOS can sometimes annotate genes that MitoFinder was not able to find. However, even with good references, MITOS can sometimes find some features, such as tRNA's and rRNA's, that MitoFinder does not, so I always run this, and only use as needed. For this pipeline, MITOS uses the contigs in the MitoFinder Final Results directory created in the previous step.  

Run the  MITOS for annotating MitoFinder contigs shell script, including the path to the directory containng your sample-specific MitoFinder directories files and the number representing the genetic code you wish to use. For most, the path should be something like: `/scratch/genomics/<USERNAME>/<PROJECT>/data/results/mitofinder_final_results/`. The genetic code will most likely be either "2" (for vertebrate mitochondrial DNA) or "5" (for invertebrate mitochondrial DNA). For other taxa, see the `.sh` or `.job ` file for a complete list. 
```
sh mitos_annotate_mitofinder.sh <path_to_mitofinder_final_results> <genetic_code>
```

Results of these analyses are saved in `<PROJECT>/data/results/mitos_mitofinder`. The results for each sample will be in a separate folder, named with the sample name.