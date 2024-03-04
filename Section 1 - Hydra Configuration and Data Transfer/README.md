## Hydra Configuration and Data Transfer

### Log into Hydra
Open the terminal app and log onto Hydra. You will need your hydra account password.

### Project-specific Directory 
Go to the the directory assigned to you for short-term storage of large data-sets. Typically this will be `/scratch/genomics/<USERNAME>`

Make a project-specific directory, with the following subdirectories: `jobs` and `data/sra`. -p allows you to create subdirectories and any parental ones that don't already exist (in this case, your project). I typically will create the same directory tree on my local computer.

```
mkdir -p <PROJECT>/data/sra <PROJECT>/jobs
```

### Hydra Jobs

We will supply "generic" hydra .job files for each program. These files will have some hydra-specific parameters pre-filled (-q, -l), but -N (job name), and -o (log name) should be changed by the user. Likewise, many application-specific parameters will also be prefilled with appropriate values, but paths and filenames will all need to be changed. At the bottom of each .job file is a brief description of the application and descriptions of each parameter listed.

Job files for all programs can be found here: [Genome skimming 2024
 job files](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/tree/main/job_files) 

Links to application-specific .job files will be in each respective section. Alternatively, you can download all the job files we will use in thi workshop here [Genome Skimming Job Files](https://github.com/SmithsonianWorkshops/Genome_Skimming_Workshop_LAB_2024/tree/cbd8251c52c64a72c2b3493bd2113870df92c777/job_files). To create your own specific job, I would copy the text of the .job file from the browser and paste it into a new text file on hydra. For example, to make a new fastqc job file:
```
nano fastqc_SRR1234567.job
```




### Globus
 We will be using the Globus to transfer data from hydra to our local computer. 

