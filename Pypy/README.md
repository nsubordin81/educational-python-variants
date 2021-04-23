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

### Interesting Features Added

### Advantages Over CPython, If Any
- Averages 4.4x faster when average is taken across all benchmarks
- Tends to run even faster on longer algorithmic code which is the very kind that usually wants it most
- Tends to use fewer memory resources than CPython when running

### Applications

### Limitations
- RPython is a restriced set of python, you can't do everything in it that you can in CPython
- CPython will always be a little ahead with new features, Pypy might be the best at keeping up though
- it is slower to warm up
- it isn't going to optimize C/C++ extensions or libs that depend on them
- CPython has optimizations built into its interpreter for things like built-in types and functions so it will still be faster

## Sources
