# Additional material

This section contains material that we are covering after the main pipeline is complete.

## Working with many samples at one time

You've seen from the work we've done this week that to run each job for each samples takes significant hands-on time and is prone to errors. Automating processing for multiple samples reduces your time working the samples through the pipeline, plus with the power of the cluster being able to run many analyze at once, you can reduce the "wall clock" time of your jobs in the analysis phase.

* *Automating job submissions*: This method takes what we've learned this week about job scripts and submits analyses for multiple jobs at one time. Using this strategy is lowest barrier to entry and the sophistication of the process (e.g. error checking, re-submissions) is determined by your scripting skills. We'll be showing one method of this type of job submission.

* *Workflow managment systems*: Another method is using a workflow management system. These submit jobs for you, do error checking (e.g. resubmitting or flagging failed jobs), incorporate decidision trees. The two most common systems used in biological data analyses are [NextFlow]<://www.nextflow.io> and [Snakemake]<https://snakemake.github.io>. There will be time investment in learning this system and modifying your job scripts, but the payoff will be able to utilize features that are built-in to the system, like resuming an interrupting workflow.

### Automating job submissions

* The modified job script is [fastqc_raw_LOOP.job]<../jobs_files/fastqc_raw_LOOP.job>
* Start start the job look we're going to use [submit_fastqc_raw_LOOP.sou]<../jobs_files/submit_fastqc_raw_LOOP.sou>

#### Adding separate log files

The `basename` command will get us the name of the file *without* the precedding path.

For example:

```
$ basename /path/to/your/sequences.fastq
sequences.fastq
```

In scripting we can capture the output of a command into a variable like this: `VAR=$(command)`

In our source file add:

```
BASE=$(basename $FILE)
```

And modify the qsub command to:

```
qsub -o logs/$BASE-fastqc-raw.log fastqc_raw_LOOP.job $FILE
```

And re-source your file:

```
source submit_fastqc_raw_LOOP.sou
```

Now check your logs...