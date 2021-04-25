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
- you can annotate the python you write with type declarations, the compiler will perform optimizations

### Interesting Features Added
- really good for building C extensions, you can write them in python with just a few extra lines
- 

### Applications

### Limitations
- Cython Maintains a list of ways their compiler generated code  is semantically incompatible with some CPython features 
	https://cython.readthedocs.io/en/latest/src/userguide/limitations.html?highlight=compatibility#limitations
- Even though Cython is a language, it is designed to help you compile CPython down to faster code, not really to replace the core language

## Sources
- “An Overview¶.” Cython, cython.readthedocs.io/en/latest/src/quickstart/overview.html. 
