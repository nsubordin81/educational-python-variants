# Jython

<!-- TOC -->
- [Reference Card](#reference-card)
    - [Changes From CPython](#changes-from-cpython)
    - [Interesting Features Added](#interesting-features-added)
    - [Applications](#applications)
    - [Limitations](#limitations)
<!-- /TOC -->

## Reference Card

### Changes From CPython
- Compiles python down to Java bytecode rather than Python bytecode and runs on the Java Virtual Machine (JVM)

### Interesting Features Added
- you can embed a python interpreter in your java programs
- you can run a python interpreter that has access to and calls java libraries
- you can write java code that calls out to python subroutines
- tested for Java compatibility up to Java 11 according to jython.org/newx
- python.org affirms it is compatible with python 2.7.2, so behavior should match CPython

### Applications
- using it for interactive testing of java code without having to mess with the build environment
- core python libraries that don't change much version to version and are better than java at things like talking to the OS
- provide a scripting language for clients of your applications
- use it for testing, either to more easily build fakes or even to setup a test bed where you make changes to your program at runtime and assert on its behavior

Directly lifted this list from jython.org's landing page: 
#### Who Uses Jython?
IBM Websphere - Use Jython to provide administrative scripting capabilities.

Apache PIG - Use Jython to support user defined functions.

ImageJ - Use Jython to provide scripted image processing.

GDA - Use Jython to script scientific experiments.

Robot Framework - A generic test automation framework for acceptance testing and acceptance test-driven development (ATDD) which runs on Jython.

TigerJython - An educational programming environment that is based on Jython.

JEM/JythonMusic - An environment for music making and creative programming using Jython.


### Limitations
- Behind Cpython by several versions   
- Not using the CPython Runtime means more work to integrate with everything that it does (C extensions, upgrades to CPython features, etc.).
- Can be slower than CPython maybe in some cases it is faster, depends on JVM interpreter wheter it has JIT compiler and also what python code is being run. If the code is optimized C code then CPython runtime woudl be faster

### Additional Information/Source Material
"Jython in Practice." Fredrik Haard. https://www.youtube.com/watch?v=VAg-UuieTUw. uploaded 7/24/2014 by EuroPython 2014.
Jython Page: https://www.jython.org/
