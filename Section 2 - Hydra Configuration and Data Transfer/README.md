## Hydra Configuration and Data Transfer

### Log into Hydra
Open the terminal app and log onto Hydra. You will need your hydra account password.
```
ssh USERNAME@hydra-login01.si.edu
```

### Project-specific Directory 
Go to the the directory assigned to you for short-term storage of large data-sets. Typically this will be `/scratch/genomics/<USERNAME>`

```
cd /scratch/genomics/<USERNAME>
```

Make a project-specific directory, with the following subdirectories: `jobs` and `data/sra`. -p allows you to create subdirectories and any parental ones that don't already exist (in this case, your project). Create the same directory tree on my local computer for later.


```
mkdir -p <PROJECT>/data/sra <PROJECT>/jobs
```

### Hydra Jobs
We will supply "generic" hydra .job files for each program. These files will have most hydra-specific parameters pre-filled (-q, -l), but -N (job name), and -o (log name) should be filled by the user. Likewise, many application-specific parameters will also be prefilled with appropriate values, but paths and filenames will all need to be changed. At the bottom of each .job file is a brief description of the application and descriptions of each parameter listed.



### Globus
 We will be using the Globus to transfer data from hydra to our local computer. 