# Additional material

This section contains material that we are covering after the main pipeline is complete.

## Working with many samples at one time

You've seen from the work we've done this week that to run each job for each samples takes significant hands-on time and is prone to errors from typos. Automating processing for multiple samples reduces your time working the samples through the pipeline, and with the power of the cluster being able to run many analyze at once, you can reduce the "wall clock" time of your jobs in the analysis phase.

There are methods to automated the submission of job files. This reduces your time working the samples through Hydra, and with the power of the cluster being able to run many analyze at once, you can speed up the total analyses are running on the cluster (that is reduced "wall clock" time).
### Automating job submissions

This method takes what we've learned this week about job scripts and submits analyses for multiple jobs at one time. Using this strategy is lowest barrier to entry and the sophistication of the process (e.g. error checking, re-submissions) is determined by your scripting skills. We'll be showing one method of this type of job submission.

### Workflow managment systems

Another method is using a workflow management system. These submit jobs for you, do error checking (e.g. resubmitting or flagging failed jobs), incorporate decidision trees. The two most common systems used in biological data analyses are [NextFlow]<://www.nextflow.io> and [Snakemake]<https://snakemake.github.io>.