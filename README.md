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
* mapreduce.Job.waitForCompletion
   * Job.submit()
      * Got a JobSubmitter
