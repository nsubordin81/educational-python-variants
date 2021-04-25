# Stackless Python

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
- Continuations and all of the things you get with them: 
	- tasklets, cooperative or multitasking on a single thread, "the number of execution contexts you can have is only limited by available memory" (krisvale)
	- channels to have tasklets communicate bidirectionally
	- there is a round robin scheduler that lets context switching from tasklet to tasklet be managed by the OS (premptive) or by each other (cooperative). (About Stackless)
- Pickling extensions were built in to further improve the efficiency of restoring tasklets that were woken up (krisvale), this is used by channels

### Applications
- EVE Online famously used Stackless to run a game with tens of thousands of concurrent users on a single server (https://www.eveonline.com/)
- Nagare is a web server that instead of just receiving and handlign requests, it treats the interaction between the website and the user as "an execution graph. When user input is required, execution on the server halts, and resumes once the user has interacted. Pickling is used not only to halt execution on the server to continue it later, it can be used in conjunction with e.g. memcached so that execution can continue on a different machine altogether." (krisvale). Nagare lets you write a series of components that contain control flow for the logic instead of having that control flow broken up into controllers like you would in other web frameworks. (https://nagare.org)

### Limitations
- Due to the bold revisions made in Stackless, it has grown apart from python in significant ways that mean it will probably remain in its limbo state of not being
adopted but not being fully abandoned either (krisvale)
- Despite the extremely innovative and undeniably cool things it has been used for, there isn't enough general usage for people to dedicate the time to keep it current. I like to call this 'the VR problem' even though I'm sure other tech suffered from it way before VR it is how I feel about both of these things
- It is a branch of CPython rather than a full on alternate implementation, contribution activity seems to go through high then low periods, not a lot of 
maintainers
- CPython has either approximated the most useful features that stackless would bring with threads (generators, coroutines, async), or in the case of greenlets ('stack slicing') and the pickling of these things, they pretty much moved it in wholesale (minus some thing like preemptively multitasking microthreads?) without disturbing Cpython as much as stackless would, further dooming its changes of ever making it into CPython (krisvale)


### Sources

- "About Stackless" Anslem Kruis. https://github.com/stackless-dev/stackless/wiki. April 4, 2021.
- "What Became Of Stackless?" krisvale's answer. Reddit. https://www.reddit.com/r/Python/comments/3rhy8o/what_became_of_stackless/. Posted Monday Nov. 9 2015 at 8:56pm EST.
- https://nagare.org
- "greenlet 1.0.0" Python Software Foundation. https://pypi.org/project/greenlet/
- "[Stackless-sprint] On greenlets" http://www.stackless.com/pipermail/stackless-dev/2004-March/000022.html
- "How Do Greenlets Work?" Answer by iMom0 and Rabih Kodeih. Stack Overflow. https://stackoverflow.com/questions/3349048/how-do-greenlets-work/17447308. posted 4/12/2014
- "Cooperative Multitasking." Denis Bilenko, gevent contributors. http://www.gevent.org/intro.html#cooperative-multitasking. 2009-2019.
- "stackless-dev/stackless" fork from cpython. github. https://github.com/stackless-dev/stackless/tree/v3.8.0b3
- "Stackless Python" https://wiki.c2.com/?StacklessPython. Last Updated October 25, 2009
