# jupyter_neuro
Interactive Python notebooks based on DartBrains 

Visit the Binder site: https://mybinder.org/v2/gh/dkp/jupyter_neuro/main

## Create Your own Environment

This Jupyter Notebook requires a dataset and several Python libraries which it explores. To really learn about these libraries, it is helpful to try variations on the commands and to try your own dataset. Trying different options is what makes Jupyter Notebooks such good learning environments.  Here's how to set up this environment using miniconda on your own computer.

```bash
# Create a new conda environment containing jupyterlab matplotlib and nilearn
conda create -n jupyter_neuro jupyterlab matplotlib nilearn
# Activate the environment
conda activate jupyter_neuro
# From inside your environment, use pip to install two more libraries
pip install pybids nltools
```

You can now use these tools on any data on your computer, just go to the directory that has your data and activate the conda environment to use the tools.  

If you'd like to use Jupyterlab to experiment, start it from your environment with the following command:

```bash
jupyter-lab
```
