---
layout: page
title: Dockerfiles
permalink: /dockerfiles/
---

Creating a `dockerfile` is an excellent method for ensuring that your replication archive is easily reproducable across different computers. When you build and run and dockerfile, you can create effcetively run your code using a virtual machine which anyone else can also access. 

Building and running a dockerfile involves two keys steps. 

1. Write a file called `Dockerfile` 
2. Build: `sudo docker build -t your-name/your-image-name .`
3. Run: `sudo docker run your-name/your-image-name

An example `Dockerfile` is included below. 

```
FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    wget \
    curl \
    git \
    vim \
    gnupg \
    software-properties-common \
    build-essential \
    ca-certificates \
    lsb-release \
    python3 \
    python3-pip \
    python3-venv \
    r-base

RUN pip3 install --upgrade pip

RUN apt-get update && apt-get install -y \
    sudo \
    apt-transport-https \
    curl \
    gnupg \
    lsb-release \
    libxml2-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    r-cran-tidyverse \
    && rm -rf /var/lib/apt/lists/*

### install specific julia and Rscript packages ###

# install r libraries with specific versions
RUN Rscript -e "install.packages(c('remotes'), repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('data.table', version='1.15.4', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('pscl', version='1.5.9', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('dplyr', version='1.1.4', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('ggplot2', version='3.5.0', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('tidyverse', version='2.0.0', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('stargazer', version='5.2.3', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('lmtest', version='0.9-40', repos='https://cloud.r-project.org/')"
RUN Rscript -e "remotes::install_version('tibble', version='3.2.1', repos='https://cloud.r-project.org/')"

# install julia 1.6.2
RUN curl -L https://julialang-s3.julialang.org/bin/linux/x64/1.6/julia-1.6.2-linux-x86_64.tar.gz -o julia.tar.gz && \
    tar -xvzf julia.tar.gz && \
    mv julia-1.6.2 /opt/julia && \
    ln -s /opt/julia/bin/julia /usr/local/bin/julia && \
    rm julia.tar.gz

# add packages
RUN julia -e 'using Pkg; Pkg.add(Pkg.PackageSpec(name="Ipopt", version="0.6.5")); Pkg.add(Pkg.PackageSpec(name="JuMP", version="0.21.10"))'

CMD ["/bin/bash"]
```

Using the above steps on this `Dockerfile` can look like the following.

```bash
sudo docker build -t nathanenglehart/dockerfile-test .
sudo docker run -it nathanenglehart/dockerfile-test
bash run.sh
exit
```

Now in `run.sh`, one can call `julia` and have it access `Ipopt` 0.6.5 and `JuMP` 0.21.10. Similarly, `R` can use the `ggplot2` library (3.5.0). All that is needed in `run.sh` is `julia 00x_script.jl` and `Rscript 00x_script.r`.

