
![snake_blueprint](https://user-images.githubusercontent.com/4014893/115093899-bf5c5500-9ee9-11eb-95e9-90124b234c50.png)


# Blueprints for a Serpent - educational-python-variants
exploration of different python implementations

# Questions To Answer

## Implementation V. Specification

### What is in a lanugage specification? 

### difference between a language specification and a specification language? 

### What is the minimum and what can optionally be specified?

## Why has python seemingly developed more implementations than other languages?

### Is this really true? What about Java, C#, C++, Ruby,  



## Why have various implementations come about? 

- Jython

- Iron Python

- Cython

- Stackless Python

- Pypy

- Starkiller

- Shedskin

### Performance

#### GIL, concurrency and parallelism

stackless python and greenlets

State of concurrency and parallelism in python, should greenlets be built in? 


### Interoperability

### Types

## What are less drastic things you can do than reimplementing? 

### C, C++, Fortran Extensions

### Libraries, Frameworks and Platforms

### Newer Python Features For Concurrency and Parallelism

## Why would you take the reimplementing python or using python variant approach over something that just works with cPython?

### cPython just doesn't have the feature and you think it should

### Using the other implementation saves you from having to write custom code

## Why doesn't Python just adopt alternate implementations? 



## What are some interesting implementations? 

## What are their limitations?

### They are often behind the curve of specification upgrades, maintained by a much smaller community
- pypy: 
- stackless: 
- shedskin:
- jython:
- iron python:

The changes made to the implementation may diverge so much with cPython that if there is a problem, 
you can't rely on the community of cPython developers to fix it. You also can't expect newer python \
features to make it to these implementations with the same speed that they hit the reference implementation. 

## Sources Consulted
https://en.wikipedia.org/wiki/Programming_language_specification
http://michael.salib.com/writings/thesis/final.pdf - starkiller thesis
