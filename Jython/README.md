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

### Applications
- using it for interactive testing of java code without having to mess with the build environment
- core python libraries that don't change much version to version and are better than java at things like talking to the OS
- provide a scripting language for clients of your applications
- use it for testing, either to more easily build fakes or even to setup a test bed where you make changes to your program at runtime and assert on its behavior

### Limitations
- Behind Cpython by several versions

### Additional Information/Source Material
"Jython in Practice." Fredrik Haard. https://www.youtube.com/watch?v=VAg-UuieTUw. uploaded 7/24/2014 by EuroPython 2014.
Jython Page: https://www.jython.org/
