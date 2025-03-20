---
layout: page
title: Example 
permalink: /example/
---

The replication checklist includes several items. Below is a skeleton of a replication example that would be an acceptable submission. 

### **Run File**

The below is an example of a shell run file `run.sh`. We strongly encourage running the use of a `Dockerfile` to run such scripts (see [here](https://pa-replication.github.io/dockerfiles/)).

```bash
#!/bin/bash

set -ex

python3 001_script1.py
Rscript 002_script2.r
julia 003_script3.jl
```

Instead of using a `Dockerfile`, one can create virtual environments using [`renv`](https://rstudio.github.io/renv/articles/renv.html), [`conda`](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html), [`venv`](https://docs.python.org/3/library/venv.html), and more. Archives should not be submitted without including materials to re-create environments.

### **Log File**

A log file confirms that you were able to successfully run your script. The below line can be appended to the `run.sh` script above. It creates a `run.log` file.

```
exec >>(tee -a run.log) 2>&1
```

### **Figures/Outputs**

All figures and outputs generated as part of the replication process should be included in the archive.

* A clear way to do this is by creating `figures` and `tables` folders

### **Compute & Runtime Details**

A `README.md` file should be included which lists the computational requirements and runtime details of the replication. An example is included below.

```
### PA Example Replication

Code details, authors, and any other relevant information should be listed here.

#### Computational requirements and runtime details

Something similar to the following should be listed. 

- This script took $X$ hours to run on **insert OS here**. 
- I used $X$ **CPU cores** and $Y$ **gigabytes of RAM**. 
- $Z$ **GPU cores / no GPU cores** are required.
```

