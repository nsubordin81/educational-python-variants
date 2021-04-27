# Working Examples

## Attribution

The files used for this demo are derivative of code found in https://github.com/helq/python-ssk by https://github.com/helq which is licensed under Creative Commons Zero v1.0 Universal and they are also 
licensed under Creative Commons Zero v1.0 Universal

Also, wow, thanks helq for coming up with a fast cython implementation of string subsequence kernel and putting it in the public domain

## Setup

To reproduce this demo, you'll need to have a Python environment with: 
- python, I'm using 3.9 
- NumPy package 
- Cython
- Pypy

*There are a couple of ways you could do this, I'll list them and then put in detailed steps for the way I did.*

### ways you could I guess: 
- installing each of these directly onto your OS from their website or your package manager of choice (homebrew, chocolate, apt-get, yum, etc.)
- docker, build image that has 'em, do all later steps in a container
- get NumPy, Pypy, and Cython as packages from some installed python/pip combo and isolate them within a virtual environment

### my way:

1. clone this repo down to your working environment
2. get the conda package manager: https://docs.conda.io/en/latest/
3. create a new conda environment `conda create -n ssk-demo python=3.9`, answer prompt with 'y' to install base packages
4. activate that environment `conda activate ssk-demo`
5. install NumPy latest version into the environment `conda install -n ssk-demo numpy`
6. install Cython from the anaconda channel into your active env (still ssk-demo) `conda install -c anaconda cython`
7. install Pypy latest version from the conda forge channel `conda install -c conda-forge pypy3.7`
8. install Jupyter Notebook from conda forge channel `conda install -c conda-forge notebook`

if all that worked, then you can start the notebook with `jupyter notebook `conda install -c conda-forge notebook`

if all that worked, then you can start the notebook with `jupyter notebook python_variants.ipynb`

ok, have fun!




## Sources
- “An Overview¶.” Cython, cython.readthedocs.io/en/latest/src/quickstart/overview.html.
- "Support Vector Machines, Part 1 of 3 Main Ideas." Youtube. https://www.youtube.com/watch?v=efR1C6CvhmE. uploaded by StatQuest With John Starner. Sept 30, 2020. 
