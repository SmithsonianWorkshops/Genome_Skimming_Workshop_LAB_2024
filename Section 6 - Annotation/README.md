## Annotation of MitoGenomes
There are multiple programs for annotation of mitochondrial genomes, including [MitoFinder](https://github.com/RemiAllio/MitoFinder), [MITOS](https://gitlab.com/Bernt/MITOS), and [MitoZ](https://github.com/linzhi2013/MitoZ). We will focus annotation using MitoFinder, but will also look at improving incomplete annotations using MITOS.

### MitoFinder
Mitofinder can perform a de-novo assembly of reads into contigs which it can then annotate, but it can also annotate external assembled contigs, which is what we will do here. We will run MitoFinder twice, once using the resultant contigs from the SPAdes assembly and once using the contigs from the GetOrganelle assembly. 

MitoFinder requires a mitochondrial genome database in GenBank (.gb) format.  It is relatively easy to generate your own reference database (see [getting reference genomes from NCBI](https://github.com/RemiAllio/MitoFinder?tab=readme-ov-file#how-to-get-reference-mitochondrial-genomes-from-ncbi) on the MitoFinder github page). You can use a general Metazoa reference database for all your assemblies, regardless of taxa, or you can create a taxa-specific database. One disadvantage to the Metazoan database is time, annotations using a large reference database can take several hours compared to much less than an hour using a smaller database.  

We have multiple phyla-specific reference databases available for usage, as well as a larger Metazoan database.

### Run MitoFinder using SPAdes Contigs

Create and submit a MitoFinder job for each of your contig files, from both your SPAdes and GetOrganelle assemblies. A generic MitoFinder job can be found here: [MitoFinder.job](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/blob/main/job_files/spades.job). 

Run the  MitoFinder for annotating spades contigs shell script, including the path to the directory containg your SPAdes contigs files, the number representing the genetic code you wish to use, and the reference database to use. For most, the path should be something like: `/scratch/genomics/<USERNAME>/<PROJECT>/data/results/spades/contigs`. The genetic code will most likely be either "2" (for vertebrate mitochondrial DNA) or "5" (for invertebrate mitochondrial DNA). For other taxa, see the `.sh` or `.job ` file for a complete list. 
The reference database should be one of: 
"Metazoa" (for the entire database)
"Annelida"
"Arthropoda"
"Bryozoa"
"Cnidaria"
"Ctenophora"
"Echinodermata"
"Mollusca"
"Nemertea"
"Porifera"
"Tunicata"
"Vertebrata"

```
sh mitofinder_annotate_spades.sh <path_to_spades_contigs> <genetic_code> <reference_database>
```
Results of these analyses are saved in `<PROJECT>/data/results/mitofinder`. The results for each sample will be in a separate folder, named with the sample name.