# Pypy 

<!-- TOC -->
- [Reference Card](#reference-card)
    - [Changes From CPython](#changes-from-cpython)
    - [Interesting Features Added](#interesting-features-added)
    - [Applications](#applications)
    - [Limitations](#limitations)
<!-- /TOC -->

## Reference Card

### Changes From CPython
- Interpreter is in CPython, not C
- Really

### Interesting Features Added
- Averages 4.4x faster when average is taken across a range of standard benchmarks
- Tends to run even faster on longer algorithmic code which is the very kind that usually wants it most
- Tends to use fewer memory resources than CPython when running
- under very active development

### Applications
- Anything you need more speed for

### Limitations
- it can be slower to 'warm up' than CPython, so not the best for running smaller programs (Bivald)
- RPython is a restriced set of python, you can't do everything in it that you can in CPython, but the restriction seems small
- CPython will always be a little ahead with new features, Pypy might be the best at keeping up though and is highly compatible with versions it has reached
- C Extensions need to be recompiled for pypy to work properly, and other constraints on compability listed here https://www.pypy.org/compat.html
- it isn't going to optimize C/C++ extensions or libs that depend on them, nor database or HTTP heavy web apps (Bivald)
- CPython has optimizations built into its interpreter for things like built-in types and functions so it will still be faster

## Sources
"PyPy" The PyPy Team. https://www.pypy.org/. 2021
"Using PyPy instead of Python for speed." Niklas Bivald. https://www.youtube.com/watch?v=1n9KMqssn54&t=712s. uploaded 10/6/2017 by PyCon Sweden.
