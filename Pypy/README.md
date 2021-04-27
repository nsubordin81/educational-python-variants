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
- Can sometimes use fewer memory resources than CPython when running
- under very active development
- The RPython Toolchain was general purpose enough to enable the Pypy team to implement the same type of JIT compiled language variant for Prolog, Smalltalk, Javascript, Io, Scheme, and Gameboy (The Pypy Team)

### Applications
- Anything you need more speed for

### Limitations
- The JIT compiler can be slower to 'warm up' than CPython, so not the best for running smaller programs (The Pypy Team)(Bivald).
- CPython will always be a little ahead with new features, Pypy might be the best at keeping up though and is highly compatible with versions it has reached
- C Extensions need to be recompiled for pypy to work properly, and other constraints on compability listed here https://www.pypy.org/compat.html
- it isn't going to optimize C/C++ extensions or libs that depend on them, nor database or HTTP heavy web apps (The Pypy Team) (Bivald)
- CPython has optimizations built into its interpreter for things like built-in types and functions so it will still be faster

## Sources
"PyPy", "Pypy-Features", "Pypy-Compatibility." The PyPy Team. https://www.pypy.org/ (/features.html, /compat.html). 2021
"Using PyPy instead of Python for speed." Niklas Bivald. https://www.youtube.com/watch?v=1n9KMqssn54&t=712s. uploaded 10/6/2017 by PyCon Sweden.
"Cython, pybind11, cffi - which tool should you choose?." Stefan Behnel. http://blog.behnel.de/posts/cython-pybind11-cffi-which-tool-to-choose.html#:~:text=When%20it%20comes%20to%20wrapping,a%20Python%20API%20for%20them.&text=CFFI%20is%20Python%20with%20a,libraries%20from%20regular%20Python%20code. Posted Sept. 15, 2018.
"Getting Started with RPython.", "The RPython Toolchain." "JIT documentation" The Pypy Project Revision 73e7c4e0b67d. https://rpython.readthedocs.io/en/latest/getting-started.html (/translation.html, /jit/index.html). Copyright 2016, accessed April 24, 2021.
