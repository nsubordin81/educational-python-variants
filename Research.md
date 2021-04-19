# Research On Language Specifications and Python Implementations

<!-- TOC -->
 - [Implementation V. Specification](#implementation-v-specification)
 - [Important Language Design Considerations](#important-language-design-considerations1)
 - [Why Are There Interesting Python Implementation Alternatives?](#why-are-there-interesting-Python-alternatives)
 - [What Less Drastic Things Can You Do Than Reimplementing The Language?](#what-are-less-drastic-things-you-can-do-than-reimplementing)
 - [Why Make An Implementation Or Use One Over Toughing It Out with cPython?](#why-would-you-take-the-reimplementing-Python-or-using-Python-variant-approach-over-something-that-just-works-with-cPython)
 - [Why Not Switch To One Of These Implementations Just Because?](#why-wouldnt-you-switch-implementations-to-one-of-these-whenever-you-need-their-features)
 - [Will These Implementations Replace CPython?](#why-doesnt-python-just-adopt-alternate-implementations-that-provide-such-nice-features)
 - [What Are Some Interesting Implementations?](#what-are-some-interesting-implementations)
 - [What Are Their Limitations?](#they-are-often-behind-the-curve-of-specification-upgrades-maintained-by-a-much-smaller-community)
 - [Sources, Read More About Language Design And Python Implementations](#sources-of-information)
<!-- /TOC -->


## Implementation V. Specification

Python.org has a list of what it recognizes as alternative implementations of the python specification, which includes IronPython, Jython, Pypy, Stackless Python, and Micro Python https://www.python.org/download/alternatives/

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
- Most of these implementations are either for browser specific interfaces, smaller footprint interpreters for embedded JS and IoT devices, JIT compilation and GraalVM supports interoperability for languages. Not as much experimentation or branching of the core runtime architecture like some of the Python ones do, but again there's webassembly. . . so I guess they are doing it their own way.
- Ruby
    - there are several implementations of Ruby. As a close cousin of Python at least in its layer of abstraction at runtime, Ruby seems to have a similar list of offshoots. Many of them are also now defunct, but there are some that are still actively maintained and these generally look to be supporting interoperabiliy with ruby and other languages or at least supporting cross compilation of ruby so it can be run as bytecode or machine lanugage. Rubinius is an interesting attempt to do what Pypy does for Python by writing an interpreter in Ruby, it is still porting over from C++ as of this writing it looks like.
- C# 
    - C# has an official standard referred to as the Common Language Infrastructure and a specification documentation site defined microsoft's page: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/introduction, so does it have alternate implementations? 
    - Before I answer, just to keep you in suspense, some news on the reference implementation front for C#: it looks like they just recently open sourced their compiler code both for the higher level Roslyn Compiler and also RyuJIT, lower level just in time compiler to translate from their intermediate language to machine code. Those are standard to .NET Core https://devblogs.microsoft.com/dotnet/the-ryujit-transition-is-complete/
    - OK, now I will answer. Yes, there are alternative implementations, though I don't see a lot of them. C# has been more proprietary for longer than the other languages on this list, so that could explain why there aren't as many, and why the few that do exist are either trying to open up usage to non-proprietary use cases (Mono, very behind the latest .NET Core versions but used by big names like Unity), or cross platform support (Elements toolchain, Xamarin)i https://en.wikipedia.org/wiki/C_Sharp_(programming_language)#Implementations

### Performance

#### GIL, concurrency and parallelism

stackless Python and tasklets allow for massive cooperative asynchronous concurrency without parallelism.

State of concurrency and parallelism in Python is that it has had support for concurrency with threads for some time and there have been significant upgrades to it in 3.2 and up https://wiki.python.org/moin/Concurrency
Python is also able to support multi core parallelism through multiprocessing. There is even support for reactive streams in python through RxPy. It seems as though you need to be more conscious of what type of concurrency you are aiming to do than with other languages as the GIL is still a concern.

There have been some attempts to remove the GIL in Pypy https://morepypy.blogspot.com/2017/08/lets-remove-global-interpreter-lock.html

A talk on concurrency in python ://www.youtube.com/watch?v=9zinZmE3Ogk&t=746s and concurrency in general. Some good points. Multiprocessing is not going to be as efficient as multithreading because threads can put things in and take things out of memory with no overhead and share state and processes cannot. Async takes away a lot of the costs of using threads for single core concurrency, but there is a lot of additional code you need to learn to write and refactor out of your existing codebase to use it properly. That being said, if you use threading wrong, the kinds of difficult to observe bugs you'll get make taking the time to learn async properly worthwhile.

### Interoperability

Sometimes it is desirable to embed python scripts inside of a slightly lower level language like Java or C#, have python compile to something that a javascript engine could run

### Types

Compilation for static type checking for speed has not been historically high on the list for standard python, but Cython
is being used for essentially this, compiling a python superset language that gives you tools for manual type declaration and optimization options down to optimized C instructions. Numba is another compiler that aims to do this, though instead of compilation it is interpreted and uses llvm and jit to speed up segements of your code. A good comparison is on this blog post: http://stephanhoyer.com/2015/04/09/numba-vs-cython-how-to-choose/

Also of interest to the topic of typing would be Guido Van Rossum's talk on the approach to typing in python 3 at PyCon 2015 https://www.youtube.com/watch?v=2wDvzy6Hgxg&t=1012s . This approach at the time was being considered internally for program correctness and other concerns type systems could assist with more than it was about speed, and it was being conducted independently of the influence of alternative python implementations.

## What Are Less Drastic Things You Can Do Than Reimplementing?

### C, C++, Fortran Extensions

You can write extensions to Python in C, C++ and even Fortran (though I didn't look into this last one very much). In addition to giving 
you speed, it enables you to define new built in Python types and also make C system calls within your code. 

However, rather than writing these extensions in C/C++, which has its own set of documentation on docs.Python.org, https://docs.Python.org/3/extending/extending.html python docs advise that you use one of the higher level tools like Cython and Numba that allow you to write these extensions in a special superset of Python

### Explore Modules, Frameworks and Platforms

There is an appetite for Python in the scientific community because it is a fully featured language that is easy to work with, you can get
something up and running quickly and iteratively with it. As a result, the community using Python for scientific applications have made a lot
of efforts towards making Python run faster either by overcoming its limitations or extending it with new libraries that are highly optimized for
the types of operations that are typically performed. There is a suite of packages like SciPy, Numpy, and Pandas, that rely on optimized math libraries like Linear Algebra Package (LAPACK) and Basic Linear Algebra Subprograms (BLAS), and also do things like suspending the Global Interpreter lock to perform parallel operations: https://developer.ibm.com/languages/Python/articles/ba-accelerate-Python/

### Newer Python Features For Concurrency and Parallelism

Core cPython has also made additions to its concurrency support in the standard library in Python 3+ to give you asynchronous capabilities for operations like I/O and also the multiprocessor package that gets around the Global Interpreter Lock (GIL) by going up one level to spawn new processes and different CPU cores that each have their own GIL.

## Why would you take the reimplementing Python or using Python variant approach over something that just works with cPython?

### cPython just doesn't have the feature and you think it should

Stackless Python and Pypy are both good examples of this. Stackless was and effort to create a Python language that would support continuations. Here's some interesting remarks around that: http://wiki.c2.com/?StacklessPython. 

Pypy was conceived from the desire to be 'Python written in Python'. It achieved Python written in a slightly restricted rPython, but also has achieved much more, like an interpreter that can generate just-in-time compilers for dynamic languages other than Python. https://rPython.readthedocs.io/en/latest/

### Using the other implementation saves you from having to write custom code

Cython is a great example of this, it allows you to write extensions in Python that is only slightly modified, so you don't have to 
go through the process of learning to write them in C/C++

If you can achieve significant performance boosts with Pypy and your code is at the right Python version then this can save you from 
having to write extensions in the first place

If you have a main application built in java or c# and you want to provide the ability for people to script plugins or 
other features in an older version of Python, then Jython or IronPython could be a good fit. In this case you really want interoperability
between the languages without having to deal with message transfer and handcoding a lot of serialization and deserialization yourself

## Why Wouldn't You Switch Implementations To One Of These Whenever You Need Their Features?

The obvious one here is just lack of support for recent language features. If one part of your application
could really benefit from just in time compilation speedup but another part relies on a 3.9 feature, as if this 
writing you can't have both with Pypy. Similarly for stackless, but if you are doing concurrency on a massive scale and
don't mind missing out on some newer features then maybe you don't mind ;)

Alternative implementations may also just not behave the way in which you would expect if using them in place of cPython, 
becauase in addition to being compatible with cPython versions, they need to be compatible with c extensions and packages 
that are built to work with cPython. You generally just don't get guarantees that the community supporting your implementation
is going to catch the wide variety of special cases that can come up 

This actually becomes even more pronounced with the interoperability versions. Jython and IronPython are both only up to version compatibility with
cPython 2.7 at the time of this writing in 2021, which means they only have support for versions of Python which are considered 
officially deprecated by the Python community, no longer receiving support or security updates

The notable exception to most of this advice for both performance and interoperability is Cython. Even though Cython offers more reassurance than
guarantee that it will be able to compile your code, it is not really as crucial, because its goal is to make it easier for your to 
write something that will run almost as fast as C but written in something that is close to the latest version of cPython. The regular
Python interpreter and VM would then be able to have your Python code call the precompiled extensions you write 


So when it comes to switching implementations just for a performance boost or because you want to interface with other language modules,
the advice I have is to really consider whether your use case is isolated enough that your decision to go with another implementation
won't paint you into a corner. For language interoperability, you can stay at the output level and write a translation layer with some common messaging format, for performance, you could optimize your code or write a c extension. You really need to have 

## Why doesn't Python Just Adopt Alternate Implementations That Provide Such Nice Features? 

I'm sure the Python developer community would have very detailed and pointed reasons for each of the alternate implementations we've covered. My view on this after studying it a fair bit is this: generally, alternative implementations of Python are willing to 
substantially change its core in order to get one very cool feature. If the changes were less drastic, then these wouldn't
be alternate implementations, they'd be modules, frameworks or some other type of extension. if you are a Python language 
developer, you already have a lot of things to be concerned with, such as not introducing incompatible changes, and 
continuing to support features that rely on the existing interpreter and VM.

Most of the alternative implementations require changing the bytecode and vm that the interpreter uses or modifying something
else core to the language (the C stack in the case of stackless). While these have stabilized into their own usable forms, 
maintainers of the language would be dealing with a lot of new complexity and fundamental shifts in the language if they were
to bring in these features. That doesn't stop them from being under consideration as PEPs though, it is just more likely that
they will either be deferred indefinitely or you'll see a more consensus driven form of them incorporated down the line
(A



## What are some interesting implementations?

Python.org and the language reference docs both list what python considers to be compatible alternative implementations to the python programming language https://www.python.org/download/alternatives/ https://docs.python.org/3/reference/introduction.html#alternate-implementations. Note that Cython is not covered here, being both a restricted python language as well as one more geared towards compiling extensions than python programs. Numba is likely also excluded for the same reason, but there are also others omitted because they aren't deemed to meet the specification corresponding to any specific python version. Here is a more broad list of alternate languages as well as interpreter and compiler variations: 

more comprehensive list of python implementations https://wiki.python.org/moin/PythonImplementations
list of python compiler projects over the years: https://github.com/pfalcon/awesome-python-compilers

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

1. Tucker, Allen B. and Robert E. Noonan. "*Programming Languages: Principles and Paradigms.*" 2nd ed., McGraw Hill, 2007.
2. https://en.wikipedia.org/wiki/Programming_language_specification
3. Python General Faq page https://docs.Python.org/3/faq/general.html
4. Oral History of Guido Van Rossum https://www.youtube.com/watch?v=Pzkdci2HDpU, Jul 26, 2018
http://michael.salib.com/writings/thesis/final.pdf - starkiller thesis
5. Python Language Reference https://docs.Python.org/3/reference/index.html
6. Python Enhancement Proposals  https://www.Python.org/dev/peps/
7. Other Java implementations, https://dwheeler.com/java-imp.html#:~:text=These%20implementations%20include%20GNU's%20gcj,by%20Microsoft%20and%20by%20Mono).
8. Lambda The Ultimate, question about Standardized languages http://lambda-the-ultimate.org/node/4111. 
