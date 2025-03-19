---
layout: page
title: 
permalink: /example/
---

The replication checklist includes several items. Below is a skeleton of a replication example that would be an acceptable submission. 

### **Run File**

```bash
#!/bin/bash

### set up environments ###
# python venv example (though R envs and/or setting up different python version is also acceptable) 

python3 -m venv /home/$USER/venv
python3 /home/$USER/venv/bin/activate
pip install -r requirements.txt
deactivate
python_env_1=/home/$USER/venv/bin/python

$python_env 001_script1.py

# subsequent scripts below e.g.

$python_env 002_script2.py
```

### **Log File**

A log file confirms that you were able to successfully run your script. The below line can be appended to the `run.sh` script above. It creates a `run.log` file.

```
exec > >(tee -a run.log) 2>&1
```

### **Figures/Outputs**

All figures and outputs generated as part of the replication process should be included in the archive.

### **Compute & Runtime Details**

A `README.md` file should be included which lists the computational requirements and runtime details of the replication. An example is included below.

```
### PA Example Replication

Code details, authors, and any other relevant information should be listed here.

#### Computational requirements and runtime details

Something similar to the following should be listed. The three most important things to note are bolded. This script took $X$ hours to run on **insert OS here** with $X$ **CPU cores** and $Y$ **gigabytes of RAM**. $Z$ **GPU cores / no GPU cores** are required.
```

