# Cython

<!-- TOC -->
- [Reference Card](#reference-card)
    - [Changes From CPython](#changes-from-cpython)
    - [Interesting Features Added](#interesting-features-added)
    - [Applications](#applications)
    - [Limitations](#limitations)
<!-- /TOC -->

## Reference Card


### Changes From CPython
- it is compiled, not interpreted

### Interesting Features Added


### Applications

### Limitations
- the main one is you will not be up to date with all CPython features


## Working Examples

### Attribution

The files used for this demo are derivative of code found in https://github.com/helq/python-ssk by https://github.com/helq which is licensed under Creative Commons Zero v1.0 Universal and they are also 
licensed under Creative Commons Zero v1.0 Universal

Also, wow, thanks helq for coming up with a fast cython implementation of string subsequence kernel and putting it in the public domain

### Setup

To reproduce this demo, you'll need to have a Python environment with: 
- python, I'm using 3.9 
- NumPy package 
- Cython
- Pypy

*There are a couple of ways you could do this, I'll list them and then put in detailed steps for the way I did.*

ways you could I guess: 
- installing each of these directly onto your OS from their website or your package manager of choice (homebrew, chocolate, apt-get, yum, etc.)
- docker, build image that has 'em, do all later steps in a container
- get NumPy, Pypy, and Cython as packages from some installed python/pip combo and isolate them within a virtual environment

*my way:*

1. clone this repo down to your working environment
2. get the conda package manager: https://docs.conda.io/en/latest/
3. create a new conda environment `conda create -n ssk-demo python=3.9`, answer prompt with 'y' to install base packages
4. activate that environment `conda activate ssk-demo`
5. install NumPy latest version into the environment `conda install -n ssk-demo numpy`
6. install Cython from the anaconda channel into your active env (still ssk-demo) `conda install -c anaconda cython`
7. install Pypy latest version from the conda forge channel `conda install -c conda-forge pypy3.7`

ok, done!

### Quick Background What We Are Showing Here

For demoing I wanted to find an example of something non-trivial to simulate an actual coding situation where writing straight CPython is insufficient performance wise and you have to start looking for 
solutions with Python alternatives. 


Scenario: Your favorite band, the Grpxlynx, just released a new single. However, in their usual style, they did it with a twist. Instead of putting out the record on Spotify, they've been posting 
thousands of random strings of alphabetic character sequences on sites all over the internet and they've hinted that in the text somewhere lies a clue to finding the song. You and a group of friends have managed to scrape down all known instances of these sequences, but you can't make heads
or tails of what they mean. There are no gaps the characters are so random that simple string distance metrics alone won't be sufficient to categorize the blocks of text. You need something better, 
and that leads you to the idea of clustering with a string subsequence kernel. 








## Sources
- “An Overview¶.” Cython, cython.readthedocs.io/en/latest/src/quickstart/overview.html. 
