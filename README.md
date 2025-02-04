# EvoBind
In silico directed evolution of peptide binders with [AlphaFold2](https://www.nature.com/articles/s41586-021-03819-2)
\
**EvoBind** designs peptide binders towards user-specified target residues using only sequence information. EvoBind accounts for adaptation of the receptor interface structure to the peptide design during optimization. This consideration of flexibility is crucial for binding.

<img src="./EvoBind.png" width="50%" height="50%"/>

AlphaFold2 is available under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0) and so is EvoBind, which is a derivative thereof.  \
The AlphaFold2 parameters are made available under the terms of the [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/legalcode) and have not been modified.
\
**You may not use these files except in compliance with the licenses.**
\
EvoBind is also available as a **Colab notebook** here: https://colab.research.google.com/github/patrickbryant1/EvoBind/blob/master/EvoBind.ipynb

# Computational requirements
Before beginning the process of setting up this pipeline on your local system, make sure you have adequate computational resources. Make sure you have an **available GPU** as this will speed up the prediction process substantially compared to CPU optimization. EvoBind assumes you have NVIDIA GPUs on your system, readily available. A Linux-based system is assumed.

# Setup
All needed packages are supplied through a Singularity image.
The only requirement for running MoLPC is therefore singularity, which can be installed by following: https://sylabs.io/guides/3.0/user-guide/quick_start.html
\
To setup this pipeline, clone this github repository:
```
git clone https://github.com/patrickbryant1/EvoBind.git
```
\
To install Singularity3 on a Linux system, do
```
bash ./src/install_singularity_ubuntu.sh
```
Then do
```
bash setup.sh
```
This script fetches the [AlphaFold2 parameters](https://storage.googleapis.com/alphafold/alphafold_params_2021-07-14.tar), installs the singularity image and downloads [uniclust30_2018_08](http://wwwuser.gwdg.de/~compbiol/uniclust/2018_08/uniclust30_2018_08_hhsuite.tar.gz) which is used to generate the receptor MSA.

# Design binders
To design binders the following needs to be specified: \
**Target residues** \
**Receptor CAs** \
**Receptor fasta sequence** \
**Peptide length** \
**Peptide centre of mass relative to the receptor CAs**

A test case is provided in **design_local.sh**. \
This script can be run by simply doing:
```
bash design_local.sh
```
