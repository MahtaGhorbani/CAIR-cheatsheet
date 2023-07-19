<!-- Output copied to clipboard! -->

<!-- Yay, no errors, warnings, or alerts! -->

<h2>CAIR System Cheat Sheet</h2>



<h3 id="cair">CAIR</h3>


This cheat sheet is created to navigate through CAIR's file management system ,LSF. LSF (Load Sharing Facility) is a workload management platform, job scheduler, for distributed high performance computing (HPC) by IBM

<h3 id="accessing">Accessing</h3>


To access the CAIR system, use the following command:
```
ssh username@server_ip
```
Mun’s servers are 

* 10.250.0.3
* 10.250.0.4
* login1.cair.mun.ca
* login2.cair.mun.ca

<h3 id="file-transfer-and-storage">File Transfer and Storage</h3>


To transfer files to and from the CAIR system, you can use the following commands:



* Scp (Secure copy) : 

```
scp filename username@serve_ipr:location 
```


* Sftp (Secure File Transfer Protocol):

```
 sftp username@server_ip
```


 To Download from server: ‘Get filename’ \n
 To Upload file: ‘Put filename’

<h3 id="modules">Modules</h3>


There are many centrally installed softwares and for some software even multiple versions. To configure the environment for a particular software version, modules are used. Modules configure your current computing environment (PATH, LD_LIBRARY_PATH, MANPATH, etc.) to make sure all required binaries and libraries are found.



* Get available modules: ''' module ava '''
* Load a module named moduleName : ''' module load moduleName '''

<h3 id="job-submission">Job Submission</h3>


To submit a job to the CAIR system, use the following command:


```
bsub [LSF options] [Job]
```




    * Job Types:
        * A single Linux command
        * A program with its path
        * A shell script passed via <
            * Example: bsub < hello.sh
    * LSF options

<table>
  <tr>
   <td>
Option 
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>-o output
   </td>
   <td>append job’s standard output to outfile
   </td>
  </tr>
  <tr>
   <td>-e errorfile
   </td>
   <td>append job’s error messages to errorfile
   </td>
  </tr>
  <tr>
   <td>-j jobname
   </td>
   <td>assign a jobname to the job
   </td>
  </tr>
</table>



<table>
  <tr>
   <td>Option
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>-q queue_name
   </td>
   <td>Submit the job to a specific queue
   </td>
  </tr>
  <tr>
   <td>-M memory_limit
   </td>
   <td>Set the maximum memory limit for the job.
   </td>
  </tr>
  <tr>
   <td>-n num_cores	
   </td>
   <td>Specify the number of CPU cores required for the job.
   </td>
  </tr>
  <tr>
   <td>-W walltime
   </td>
   <td>Set the maximum wall time limit for the job.
   </td>
  </tr>
</table>




* Monitor a job :

    ```
 bjobs [options]
```



<table>
  <tr>
   <td>
Bjobs options
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>(no option)
   </td>
   <td>list all your jobs in all queues
   </td>
  </tr>
  <tr>
   <td>-p
   </td>
   <td>list only pending(waiting) jobs and indicate why they are pending
   </td>
  </tr>
  <tr>
   <td>-r or -a
   </td>
   <td>List only running jobs
   </td>
  </tr>
  <tr>
   <td>-d
   </td>
   <td>list only done job (finished within the last hour)
   </td>
  </tr>
  <tr>
   <td>-l
   </td>
   <td>display status in long format
   </td>
  </tr>
  <tr>
   <td>-w
   </td>
   <td>display status in wide format
   </td>
  </tr>
  <tr>
   <td>-j jobname
   </td>
   <td>show only job(s) called jobname
   </td>
  </tr>
  <tr>
   <td>-a
   </td>
   <td>Show 
   </td>
  </tr>
</table>


<h3 id="queues-information">Queues Information:</h3>


In the context of the CAIR system, a queue represents a specific category or group of computational resources and policies for job execution. Each queue may have different characteristics such as priority, maximum job runtime, and resource allocation. Understanding the queues available on the system can help you choose the appropriate queue for submitting your jobs based on their requirements and priority.



* Get a list of all queues with their properties

    ```
bqueues
```



Additionally, you can often obtain further details about a specific queue by using the ‘bqueues -l queue_name’ command.

<h3>Job Structure</h3>


A Job structure should typically contain following information


```
#!/bin/bash
#BSUB -J jobname
#BSUB -o output.log
#BSUB -e error.log
#BSUB -n num_cores
#BSUB -W walltime

# Load required modules
module load moduleName

# Commands to execute the job

```

