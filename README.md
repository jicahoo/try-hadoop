# try-hadoop

## Steps
* Step 1: Git clone this repo.
* Step 2: mkdir input in try-hadoop, and copy some text files into input folder.
* Step 3: radle run
* Step 4: Check the result under folder output under try-hadoop.


## Debug Tips
* How to make the WordCount reference to source code not jar in IntelliJ?
    * 1. Open Project structure
    * 2. Add module dependency for try-hadoop module.
    * 3. Remove jar dependency (like a hack.)
    
## The flow of execution:
### Main Thread:
* mapreduce.Job.waitForCompletion
   * Job.submit()
      * Got a JobSubmitter
      * UserGroupInformation.doAs
         * jobSubmitter.submitInternal()
            * Configuration conf = job.getConfiguration()
            * addMRFrameworkToDistributedCache(conf);
            * JobID jobId = submitClient.getNewJobID(); #submitClient is a reference to LocalJobRunner
            * int maps = writeSplits(job, submitJobDir)
               * writeNewSplits
                  * FileInputFormat.getSplits()
            * writeConf(conf, submitJobFile); #Write job.xml
            * status = submitClient.submitJob(jobId, submitJobDir.toString(), job.getCredentials());
               * Job job = new Job(JobID.downgrade(jobid), jobSubmitDir); #Job is inner class of LocalJobRunner and also a JavaThread. It will start a thread.
   * mapreduce.Job.monitorAndPrintJob

### Map thread:
LocalJobRunner.Job.MapTaskRunnable.run:
* TODO

### Reduce thread
LocalJobRunner.Job.ReduceTaskRunnable
* TODO
