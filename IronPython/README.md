# IronPython

<!-- TOC -->
- [Reference Card](#reference-card)
    - [Changes From CPython](#changes-from-cpython)
    - [Interesting Features Added](#interesting-features-added)
    - [Applications](#applications)
    - [Limitations](#limitations)
<!-- /TOC -->

## Reference Card

### Changes From CPython
Not running in the CPython runtime, it is running in .NET core's Common Language Runtime (CLR), using the Intermediate Language expected by that instead of the python bytecode.

### Interesting Features Added
- You can embed python in C# and use it to expose the ability for users of your application to script modules for it
- you can call to the .NET framework APIs directly from python, so you can have interactive sessions where you test out your .NET invocations without the overhead of building
- With a little extra code, you can also have .NET interface with a lot of python code, though based on what I've read this doesn't just work out of the box
- supported by the .NET foundation, so it isn't experimental or likely to drop off completely in support
- has type integration with .NET types, so for example you could use a python list comprehension over any IEnumerable type in C#
- python.org affirms it is compatible with python 2.7.2, so behavior should match CPython
- No GIL because you are on the .NET CLR
- Benefit from the .NET RyuJIT just in time compiler for execution, so depending on whether the python code being run has a lot of cpython optimizations or optimized C libraries that CPython is set up to run efficiently, it may be faster or slower than CPython at runtime.


### Applications
writing your own interpreter inside a .NET program that piggybacks off of the Iron Python interpreter
doing interactive testing of simple python code that can call into .NET assemblies without dealing with the build environment, you don't need to compile first
You could write whole applications in python that depend on .NET libraries, or with some

### Limitations
IronPython3 (compatibility with CPython 3.x major release) is still under development, has been for some time, it is community driven open source. 
Not using the CPython Runtime means more work to integrate with everything that it does (C extensions, upgrades to CPython features, etc.).

### Additional Information/Source Material
"IronPython." Louis Yang. https://www.youtube.com/watch?v=f2mSvqEQ66w uploaded 4/8/2015 by Louis Yang.
"ironpython-vs-python-net." Joan Venge and Reed Copsey. https://stackoverflow.com/questions/1168914/ironpython-vs-python-net. answered Dec. 27, 2011.
"IronPython the Python Programming Language For .NET." .NET Foundation. https://ironpython.net/. 
