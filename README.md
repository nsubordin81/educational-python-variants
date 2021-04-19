
![snake_blueprint](https://user-images.githubusercontent.com/4014893/115093899-bf5c5500-9ee9-11eb-95e9-90124b234c50.png)


# Blueprints for a Serpent - educational-python-variants
exploration of different python implementations

## Disclaimer and Purpose of This Page
 I am not a programming language designer, compiler author, or someone who actively develops on the core feature set of python or anoth er programming language. At least not yet :). I am an application programmer with an interest in comparing language implementations and the consequences they have for application programmers. Many of the broad and deep topics covered in this repository regarding performance optimization and language implementation I am now familiar with but have not done enough sufficient experimentation with to call myself any kind of expert. 

The purpose of this repository and the presentation it accompanies is to consolidate and share some of what I've learned in 
trying to understand the benefits of python's approach to language specification and some of the implementations that have 
resulted from it, as well as efforts to achieve the same performance and type safety goals within the reference implementation
CPython. I have made an effort to both cite sources for instances where I got an idea from somewhere else, and also call
out when I'm taking a leap and forming my own opinions based upon what I've read. I hope this can serve as an accelerated 
start for you if you are interested in learning more about these topics. Thank you for reading!

## Repo Navigation

- The [Research](Research.md) markdown page contains a cleaned up version of notes I took when digging into this topic

- There are directories in the repo for some of the more popular python implementations (with the 
notable exception of cPython). They may not all have code samples but each should have at least a description 
and some reference card information talking at a high level about their motivations, features, side benefits, and limitations.
If you are interested in contributing more implementation versions, let me know and I can add you as a contributor!

- In some cases, there will be code samples in the directories demonstrating usage of the target implementation. In 
these cases the README in that directory will attempt to provide adequate instructions for how to set up and run the 
demonstrations.
