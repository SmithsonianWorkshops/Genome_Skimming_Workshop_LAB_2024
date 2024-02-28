## SRA Data
Before we start genome skimming, we need read data to analyze. We have chosen some Sequence Read Archive (SRA) data that we have tested for you to run your analyses on. 

>"The SRA is NIH's archive of high-throughput sequencing data and is part of the International Nucleotide Sequence Database Collaboration (INSDC) that includes the NCBI Sequence Read Archive (SRA), the European Bioinformatics Institute (EBI), and the DNA Database of Japan (DDBJ). Data submitted to any of the three organizations are shared among them."

https://www.ncbi.nlm.nih.gov/sra


```module load bioinformatics/sratoolkit```

```vdb-config --interactive```

```prefetch --option-file SraAccList.csv```