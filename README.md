**Author**: Dianne Patterson <dkp@email.arizona.edu>      
**Date Created**: 2022-08-12   
**Tool Test** (Name and version): jupyter     
**Dataset**: downloaded from site          
**Download Tool from**: https://dartbrains.org/content/Introduction_to_Neuroimaging_Data.html       
**Tool Documentation is available at**: https://dartbrains.org/content/Introduction_to_Neuroimaging_Data.html     
**Tool Description**: neuroimaging data with Jupyter 

----------------

# Project Structure

This is a project to test the software tool jupyter.
- The **code** directory contains the Python Notebooks
- The **data** directory contains **inputs** and **outputs**
- data/inputs contains a BIDS dataset for use with the notebook

Download the project from XXX, unzip it and navigate into the jupyter_neuro directory:

```bash
├── README.md
├── code
│   ├── Introduction_to_Neuroimaging_Data.ipynb
│   └── README.md
└── data
    ├── inputs
    └── outputs
```



---

# Create a Jupyter Environment in Conda

This Jupyter Notebook requires a dataset and several Python libraries which it explores. To really learn about these libraries, it is helpful to try variations on the commands and to try your own dataset. Trying different options is what makes Jupyter Notebooks such good learning environments.

```bash
# Use the command line to create a new conda environment containing jupyterlab matplotlib and nilearn
conda create -n jupyter_neuro jupyterlab matplotlib nilearn
# Note the same name is used for the directory and the environment.  This is certainly not necessary, it is just a good name ;)
conda activate jupyter_neuro
# From inside your environment, use pip to install more libraries
pip install pybids nltools wget hcp-utils
```

Use `conda list` to check that all the necessary libraries were installed

Dataset: Copied contents of this BIDS dataset: `/Volumes/Main/Working/Datasets/Kielar/sub-219_bids`
to `/Volumes/Main/Working/Tool_Testing/jupyter/data/inputs`

Create a cookie cutter directory to practice in.  Copied their notebook to code

`jupyter-lab`

Double-click the `Introduction_to_Neuroimaging_Data.ipynb` in the code directory to get started.

God help you if you try this on the apporto machine.



---



# Binder

Watch this excellent youtube video on creating a binder site: https://www.youtube.com/watch?v=owSGVOov9pQ&t=137s

You need a github site: See https://github.com/dkp/jupyter_neuro

## DATA

I have separated the data from the github site.  The data is on OSF and I retrieve it with wget

```python
import wget

site_url = 'https://osf.io/5q3m8/download'
wget.download(site_url)
```

Unzip it: 

```python
import zipfile

with zipfile.ZipFile("Jupyter_neuro_data.zip","r") as zip_ref: 
    zip_ref.extractall(path=None)
```

Remove the zip file:

```python
import os

if os.path.exists("Jupyter_neuro_data.zip"):
   os.remove("Jupyter_neuro_data.zip")
```



## requirements.txt

You need a **requirments.txt** on that github site.  Rather than including everything in the `conda list` output, it is reasonable to just include those libraries you explicitly installed:

```bash
conda list | grep pybids
pybids          0.15.1          pypi_0  pypi
conda list | grep matplotlib
matplotlib        3.5.2      py310h2ec42d9_0  conda-forge
matplotlib-base      3.5.2      py310h4510841_0  conda-forge
matplotlib-inline     0.1.3       pyhd8ed1ab_0  conda-forge
conda list | grep nilearn
nilearn          0.9.1       pyhd8ed1ab_0  conda-forge
conda list | grep nltools
nltools          0.4.5          pypi_0  pypi
conda list | grep wget
wget           3.2           pypi_0  pypi
```

Here's my requirements.txt

```bash
# Python libraries
hcp-utils==0.1.0
matplotlib==3.5.2  
matplotlib-inline==0.1.3 
pandas==1.4.3
nibabel==4.0.1
nilearn==0.9.1
nltools==0.4.5
numpy==1.23.1
pybids==0.15.1
scikit-learn==1.1.1
scipy==1.8.1
wget==3.2
```

Here's my binder site:

https://mybinder.org/v2/gh/dkp/jupyter_neuro/main

Note that there is no login for binder.  Rather, given a github site (or other repo), it builds a docker container based on the notebook and the requirements.txt file.  If something changes, it rebuilds.

The first time II built I got an error related to one of the requirements (matplotlib base).  I removed that requirement and it rebuilt just fine.  I tested fully.  It works.



