# Research On Language Specifications and Python Implementations

<!-- TOC -->
[Implementation V. Specification](#Implementation V. Specification)
[Important Language Design Considerations](#Important language design considerations)



## Implementation V. Specification

### What is a language specification? 

Language specifications are the documentation of what it means to write a program in that language, 
so that implementors of the language can have consensus on what is and is not part of the language.

Some languages have gone the route of having a standards body actually maintain a standardization for their language. 
Some prominent standards organizations that perform this are ANSI, ISO, ECMA, and IEEE. A (probably not comprehensive) list of 
languages that have been standardized by these orgs includes:<sup>8</sup>
- Ada
- APT (a numerical control language)
- Basic
- C
- C++
- C#
- Cobol
- Common Lisp
- Dart
- Dibol
- Eiffel
- Forth
- Fortran
- Javascript
- Mumps/M
- PANCM
- Pascal
- PL/B (aka Databus)
- PL/I
- Rexx
- Ruby
- Smalltalk, SQL

and more as shown here: https://en.wikipedia.org/wiki/Comparison_of_programming_languages 

Python's standard is maintained apart from these organizations as described below. The rigor of the ANSI and ISO standards 
is criticised by some because the languages become so stable they fail to be open to changes from the outside. For a low 
level language like C this may very well be appropriate, but that is one of the advantages of Python's niche. 

### Python's Programming Language Specification

case Python's specification is the Python language reference and lives here: https://docs.Python.org/3/reference/index.html<sup>5</sup>

Note that the very first section in the reference implementation points out that everything except for syntax
and lexical analysis is described in natural language, and that this is intentional because this is where
freedom to extend comes from. 

The document also mentions that CPython is the widespread reference implementation and implementation notes
are provided throughout the document where special considerations having to do with that implementation.

So cPython is the 'de facto' implementation of Python, but even in cPython's case there are implementation details that
get in the way of the abstract definition of the language that the Python Language Reference attempts to provide. And,
arguably, that's a good thing because it means cPython and the other implementations aren't fully constrained by these standards.

### History of Python's specification<sup>2, 3, 4</sup>

Guido Van Rossum shared the code first time Feb 1991 0.9.0. The original language was in some ways 
a reaction to limitations in the languages he was working with at the time (ABC not extensible, 
Amoeba system calls not accessible from Bourne shell or C scripts), which may partly explain 
why Python's design is so extensible that we have alternative implementations surfacing.

From that time, the Python community has been involved but also guided by Rossum, and several 
mechanisms have come about as a process for enhancing the language. the semantic versioning has 
remained in place, with Major.Minor.Release(+, a0) as is commonplace to find on many software projects
now. Each of these versions may require an upgrade to the overall language specification. This is
why if you go to the language reference page you can select from the most recent release version of 
each minor version of Python to read a version of the reference tailored to that version of the
CPython language. 

There is a lot of history on the evolution of Python and lots of archives of conversations because 
of the high community involvement. For example, the decision to do a major version upgrade of 
Python from 2 to 3 that had some non-backwards compatible changes to, amongst other things, 
remove redundant paths to the same functionality. Not really in scope for this research but all
of these docs are fairly easy to find, either linked to Python.org or published elsewhere.

On the language development side there is also a tracking mechanism for enhancement requests that is 
open to the developer community and members of the public to read Python Enhancement Proposals (PEP). 
These can be informational but are generally proposals for changes to the language, with specific 
language about what would be required and what the benefits would be. 
 https://www.Python.org/dev/peps/<sup>6</sup>

### difference between a language specification (a.k.a standard or definition) and a specification language?

This is somewhat of a non-sequitor, but for those who might have been confused about the similar naming like I was, 
Specification languages are languages created for determining program correctness.<sup>1</sup> 
if I write a program that is supposed to add to numbers and return their sum, 
a specification language would provide me a way to prove that the program will 
find the sum for any valid inputs. 

So the difference could be simply described as "one tells you how language A is supposed to implemented, 
another tells you whether a program in language A was implemented correctly"

## Important language design considerations<sup>1</sup>

The three below topics, as well as other cross cutting ideas, are all fundamental to 
language design and need to be represented in some way in the language specification.

Syntax

Answers the question, how do I know this program's structure is correct? What words are ok
and where can I put them?

In language design, syntax definition is mostly accomplished through context free grammars (CFGs).

Names and Types

What is the vocabulary of the language? How does the language bind names, how does scoping work? 
What are the values that a program can perform operations on, a.k.a the types? what kind of 
type system is made available for language users so they can understand how to write operations, 
how can the language protect users from making mistakes through its knowledge of types?

Semantics

Just like in natural language, semantics are the meaning of the programming statements. When 
a statement is executed, what does it mean? What actually happens to the variables during an 
assignment? How are expressions evaluated? As covered in <sup>1</sup>, There is a lot of 
value in building Semantic models that aren't tied to one particular choice of machine, 
and Python accomplishes this.

## Why Are There Interesting Python Alternatives? 

Some (subjective) theories were discussed in other sections, but will repeat them here and elaborate for good measure:

- Guido Van Rossum wanted a general purpose programming language that was extensible as an early goal of 
  Python in the 1990s.
    - despite having formal descriptions of lexical and syntactical concerns, the semantic model is described with natural language
    - CPython as the reference implementation doesn't stop others from dreaming of other ways for interpretation, compilation and hardware virtualization to happen
- Python has had strong community support from the beginning, developers fall in love with how expressive and simple it is, so they would rather rewrite it than use another language
- Python is deemed a Higher Level Language (HLL) by most.
    - HLLs tend to be interpreted. Interpreters for HLLs are one more abstraction layer that can be substituted
    - interpreted languages tend to also have performance issues
- The Python community likes to keep their standard reference implementation familiar and carefully control its feature set, but they also embrace the existence of other implementations of the language


### Is Python alone with this branching behavior? What about Java, C#, C++, Javascript, Ruby, etc. which have been around a while? 

Other languages do have alternate implementations, Python is not unique in this aspect. However, Python may be unique in that it celebrates this fact somewhat, 
is proud of the malleability of its spec and advertises and encourages implementations that aren't the standard. Other languages like Java have alternate implementations, and for some of the same reasons. More often than not, these alternative implementations are just trying to enable a different group of users than the reference implementation, like people coding for browsers, embedded devices, coming from other languages, or looking for higher performance. Here are some 
reasons for alternate implementaitons or at least partial (compiler, interpreter, etc.) for other languages: 

- Java<sup>7</sup>
    - As Java became more commercial and closed over the years by Sun and Oracle, open source implementations (e.g. OpenJDK) offer a way to use Java without the licensing and litigation concerns
    - There are many compilers and transpilers both open source and proprietary that compile bytecode to machine code to run faster on target architectures
    - just like Pypy, Java has implementations that are looking at performance boosts from JIT compilers
    - Also similar to Pypy, there is a JVM written in Java
- JavaScript
    - ECMAScript is the specification, and there are a variety of different 'engines' acting as interpretors for javascript, a lot more probably than Python generally https://en.wikipedia.org/wiki/List_of_ECMAScript_engines
- Most of these implementations are either for browser specific interfaces, smaller footprint interpreters for embedded JS and IoT devices, JIT compilation and GraalVM supports interoperability for languages. Not as much experimentation or branching of the core runtime architecture like some of the python ones do, but again there's webassembly. . . so I guess they are doing it their own way.
- Ruby
    - there are several implementations of Ruby. As a close cousin of python at least in its layer of abstraction at runtime, Ruby seems to have a similar list of offshoots. Many of them are also now defunct, but there are some that are still actively maintained and these generally look to be supporting interoperabiliy with ruby and other languages or at least supporting cross compilation of ruby so it can be run as bytecode or machine lanugage. Rubinius is an interesting attempt to do what Pypy does for Python by writing an interpreter in Ruby, it is still porting over from C++ as of this writing it looks like.
- C# 
    - C# has an official standard referred to as the Common Language Infrastructure and a specification documentation site defined microsoft's page: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/introduction, so does it have alternate implementations? 
    - Before I answer, just to keep you in suspense, some news on the reference implementation front for C#: it looks like they just recently open sourced their compiler code both for the higher level Roslyn Compiler and also RyuJIT, lower level just in time compiler to translate from their intermediate language to machine code. Those are standard to .NET Core https://devblogs.microsoft.com/dotnet/the-ryujit-transition-is-complete/
    - OK, now I will answer. Yes, there are alternative implementations, though I don't see a lot of them. C# has been more proprietary for longer than the other languages on this list, so that could explain why there aren't as many, and why the few that do exist are either trying to open up usage to non-proprietary use cases (Mono, very behind the latest .NET Core versions but used by big names like Unity), or cross platform support (Elements toolchain, Xamarin)i https://en.wikipedia.org/wiki/C_Sharp_(programming_language)#Implementations

### Performance

#### GIL, concurrency and parallelism

stackless Python and greenlets

State of concurrency and parallelism in Python, should greenlets be built in? 


### Interoperability


### Types

## What are less drastic things you can do than reimplementing? 

### C, C++, Fortran Extensions

### Libraries, Frameworks and Platforms

### Newer Python Features For Concurrency and Parallelism

## Why would you take the reimplementing Python or using Python variant approach over something that just works with cPython?

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
- iron Python:

The changes made to the implementation may diverge so much with cPython that if there is a problem, 
you can't rely on the community of cPython developers to fix it. You also can't expect newer Python \
features to make it to these implementations with the same speed that they hit the reference implementation. 

## Sources Of Information 
(want more depth? I highly recommend 1, and thanks to Python and other implementations for generally being very good about documentation)

1. Programming Languages, Principles and Paradigms Allen Tucker, Robert Noonan
2. https://en.wikipedia.org/wiki/Programming_language_specification
3. Python General Faq page https://docs.Python.org/3/faq/general.html
4. Oral History of Guido Van Rossum https://www.youtube.com/watch?v=Pzkdci2HDpU, Jul 26, 2018
http://michael.salib.com/writings/thesis/final.pdf - starkiller thesis
5. Python Language Reference https://docs.Python.org/3/reference/index.html
6. Python Enhancement Proposals  https://www.Python.org/dev/peps/
7. Other Java implementations, https://dwheeler.com/java-imp.html#:~:text=These%20implementations%20include%20GNU's%20gcj,by%20Microsoft%20and%20by%20Mono).
8. Lambda The Ultimate, question about Standardized languages http://lambda-the-ultimate.org/node/4111. 
