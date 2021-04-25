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

## Setting the Stage With A Pretend Scenario

For demoing I wanted to find an example of something non-trivial to simulate an actual coding situation where writing straight CPython is insufficient performance wise and you have to start looking for 
solutions with Python alternatives. 


Scenario: Your favorite band, 2 Pegasus Tasks, just released a new single. However, in their usual style, they did it with a twist. 

Instead of distributing the song on Spotify or some other distribution platform, for its initial release they segmented  the audio file binary into tiny substrings and then inserted them according to a secret pattern into a bunch of longer strings to create an internet scavenger hunt. Any group that is able to piece the song together gets a cash prize on the condition that they don't share it or how they got it with others. They have provided a preliminary list of 300 strings, 100 of which the've confirmed do contain a chunk of the song, and 200 of which don't.

You and a group of friends have managed to scrape down all known instances of these string sequences and tried some linear but you can't make heads or tails of what they mean. When you analyze the sequences by hand, sometimes you think you've found a pattern but then another example breaks it. It definitely looks like the function for the pattern will be non-linear in nature.

So you have the idea to use a Support Vector Machine based on a string kernel to learn a boundary between what is part of the pattern and what is not in higher dimensional space. You find a whitepaper about string subsequence kernels that looks like just what you need. You search through libraries online like Scikit Learn and NLTK but in this imaginary scenario, you can't find a decent implemntation of this kernel function anywhere, so you'll have to write your own.

### With Just CPython

After pouring over the whitepaper and maybe some supplemental material to make sure you understand the concepts, you are able to create an implementation of the string-subsequence kernel. You 
are ready to run it, let's simulate that by going to an older revision of our example code which is just written in CPython with some profiling lines to show us how fast it is. 





### with just Cython

So moving to the latest version of helq's code, skipping all the hard work they did to optimize this, let's pretend we did it. So we'll compile those most recent Cython files and see how fast they ran. 

This example uses the 









## Sources
- “An Overview¶.” Cython, cython.readthedocs.io/en/latest/src/quickstart/overview.html. 
