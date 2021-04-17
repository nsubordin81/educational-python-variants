
![snake_blueprint](https://user-images.githubusercontent.com/4014893/115093899-bf5c5500-9ee9-11eb-95e9-90124b234c50.png)


# Blueprints for a Serpent - educational-python-variants
exploration of different python implementations

# Questions To Answer

## Implementation V. Specification

### What is a language specification? 

Language specifications are the documentation of what it means to write a program in that language, 
so that implementors of the language can have consensus on what is and is not part of the language.

Some languages have gone the route of having a standards body actually maintain a standardization for their language. 
Two prominent standards organizations that perform this are ANSI and ISO. A (probably not comprehensive) list of 
languages that have been standardized by these orgs includes:<sup>8</sup>
- Ada
- APT (a numerical control language)
- Basic
- C
- C++
- Cobol
- Common Lisp
- Dibol
- Forth
- Fortran
- Mumps/M
- PANCM
- Pascal
- PL/B (aka Databus)
- PL/I
- Rexx
- Smalltalk, SQL

Python's standard is maintained apart from these organizations as described below. The rigor of the ANSI and ISO standards 
is criticised by some because the languages become so stable they fail to be open to changes from the outside. For a low 
level language like C this may very well be appropriate, but that is one of the advantages of Python's niche

### Python's Programming Language Specification

Python's specification is the python language reference and lives here: https://docs.python.org/3/reference/index.html<sup>5</sup>

Note that the very first section in the reference implementation points out that everything except for syntax
and lexical analysis is described in natural language, and that this is intentional because this is where
freedom to extend comes from. 

The document also mentions that CPython is the widespread reference implementation and implementation notes
are provided throughout the document where special considerations having to do with that implementation.

So 

### History of Python's specification<sup>2, 3, 4</sup>

Guido Van Rossum shared the code first time Feb 1991 0.9.0. The original language was in some ways 
a reaction to limitations in the languages he was working with at the time (ABC not extensible, 
Amoeba system calls not accessible from Bourne shell or C scripts), which may partly explain 
why python's design is so extensible that we have alternative implementations surfacing.

From that time, the python community has been involved but also guided by Rossum, and several 
mechanisms have come about as a process for enhancing the language. the semantic versioning has 
remained in place, with Major.Minor.Release(+, a0) as is commonplace to find on many software projects
now. Each of these versions may require an upgrade to the overall language specification. This is
why if you go to the language reference page you can select from the most recent release version of 
each minor version of python to read a version of the reference tailored to that version of the
CPython language. 

There is a lot of history on the evolution of python and lots of archives of conversations because 
of the high community involvement. For example, the decision to do a major version upgrade of 
python from 2 to 3 that had some non-backwards compatible changes to, amongst other things, 
remove redundant paths to the same functionality. Not really in scope for this research but all
of these docs are fairly easy to find, either linked to python.org or published elsewhere.

On the language development side there is also a tracking mechanism for enhancement requests that is 
open to the developer community and members of the public to read Python Enhancement Proposals (PEP). 
These can be informational but are generally proposals for changes to the language, with specific 
language about what would be required and what the benefits would be. 
 https://www.python.org/dev/peps/<sup>6</sup>

### difference between a language specification (a.k.a standard or definition) and a specification language?

This is somewhat of a non-sequitor, but for those who might have been confused about the similar naming like I was, 
Specification languages are languages created for determining program correctness.<sup>1</sup> 
if I write a program that is supposed to add to numbers and return their sum, 
a specification language would provide me a way to prove that the program will 
find the sum for any valid inputs. 

So the difference could be simply described as "one tells you how language A is supposed to implemented, 
another tells you whether a program in language A was implemented correctly"

### Important language design considerations<sup>1</sup>

Syntax
Answers the question, how do I know this program's structure is correct? What words are ok
and where can I put them?

This is mostly accomplished through context free grammars

Names and Types

Semantics

### What is the minimum and what can optionally be specified?

A minimum specification is probably a formal description of syntax and then 
some description of the semantics. Without a reference implementation though that still 
leaves a lot to be guessed by any would be implementor of the language

## Why has python seemingly developed more implementations than other languages?

Some theories were discussed above, but will repeat them here for good measure:

- Guido Van Rossum wanted a general purpose programming language that was extensible as an early goal of 
  Python in the 1990s.
    - despite having formal descriptions of lexical and syntactical concerns, the semantic model is described with natural language
    - CPython as the reference implementation doesn't stop others from dreaming of other ways for interpretation, compilation and hardware virtualization to happen
- Python has had strong community support from the beginning, developers fall in love with how expressive and simple it is, so they would rather rewrite it than use another language


### Is this really true? What about Java, C#, C++, Javascript, Ruby, etc. which have been around a while? 

Other languages do have alternate implementations, Python is not unique in this aspect. However, Python may be unique in that it celebrates this fact somewhat, 
is proud of the malleability of its spec. Other languages like Java have alternate implementations, but not so many that are trying to do something fundamentally 
different. More often than not, these alternative implementations are just trying to enable a different group of users than the reference impl. Here are some 
reasons for alternate implementaitons or at least partial (compiler, interpreter, etc.) for other languages: 

- Java<sup>7</sup>
    - As Java became more commercial and closed over the years by Sun and Oracle, open source implementations (e.g. OpenJDK) offer a way to use Java without the licensing and litigation concerns
    - There are many compilers and transpilers both open source and proprietary that compile bytecode to machine code to run faster on target architectures
    - just like Pypy, Java has implementations that are looking at performance boosts from JIT compilers
    - Also similar to Pypy, there is a JVM written in Java


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
1. Programming Languages, Principles and Paradigms Allen Tucker, Robert Noonan
2. https://en.wikipedia.org/wiki/Programming_language_specification
3. Python General Faq page https://docs.python.org/3/faq/general.html
4. Oral History of Guido Van Rossum https://www.youtube.com/watch?v=Pzkdci2HDpU, Jul 26, 2018
http://michael.salib.com/writings/thesis/final.pdf - starkiller thesis
5.
6.
7. Other Java implementations, https://dwheeler.com/java-imp.html#:~:text=These%20implementations%20include%20GNU's%20gcj,by%20Microsoft%20and%20by%20Mono).
8. Lambda The Ultimate, http://lambda-the-ultimate.org/node/4111. 