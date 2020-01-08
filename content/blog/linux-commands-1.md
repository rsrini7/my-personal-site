+++
title = "Linux Commands 1"
description = "Documentation of my experiments with linux commands"
date = 2020-01-07T15:37:58+01:00
tags = ["linux","cli"]
categories = []
+++

## Linux Commands

### Get Init Process

```bash
ps -f 1
```

### Fork & Exec

    parent (ex: bash) -> child (ex ls -l) 
		 ls -l command from bash forks the new process and executing using "exec"
		 parent returns back once child finishes its work (exec ends once the process completes)
		 ex: exec ls -l (it will close current shell)


### Suspend & Restore the running process

    Suspend the current running process in foreground : ctrl + z (equivalent to below command)
    Note: kill -20 means SUGTSTP and Stopped state
```bash
kill -20 [pid]
```
    To get process with hierarchy:  
```bash
ps f 
```    
    
    Column: STAT values::: 
      T -> suspended state 
      S -> Running state 

      
Jobs

    To see running jobs

```bash
jobs
```
    To restore the suspended process as foreground : 
```bash
fg #it resume on current process, if only one job
```    
      
    To restore the suspended process as background : 
```bash
bg #it resume on current process, if only one job
```        
      
    Multiple jobs running in background and to bring foreground :
```bash
fg %{job_number} #jobs command will give job_number
```    

    Note: jobs shows + and - after job number.
      '+' means last job sent to bg
      '-' means last to previous job sent to bg
      fg / bg : equivalent to kill -18 [pid] . '-18' means SIGCONT


### Kill

    List of kill signals:
```bash
kill -l
```
Kill Processes:

    sends sigterm: Terminated state in jobs queue
    Gradual shutdown
```bash
kill -15 [pid]  #default - without number also same
```
	sends sigint : 
```bash
kill -2 [pid]
```      
	sends sighup : 
```bash
kill -1 [pid]
```      
	sends sigkill : force kill
    Abrupt shutdown
```bash
kill -9 [pid]
```      
