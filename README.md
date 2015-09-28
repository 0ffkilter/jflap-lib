jflap-lib
==============

Jflap-lib is an improved version of JFLAP 7.0 to be used as a library and a command line tool, specially useful for building auto-grading tools.

## What is JFLAP?

JFLAP is an extremely useful software for teaching and learning about formal languages. According to [jflap.org](jflap.org), "JFLAP is software for experimenting with formal languages topics including nondeterministic finite automata, nondeterministic pushdown automata, multi-tape Turing machines, several types of grammars, parsing, and L-systems". JFLAP is mantained by [Susan H. Rodger](https://users.cs.duke.edu/~rodger/) et al. from the Department of Computer Science at Duke University.

## What is jflap-lib?

This project is a minor modification of the original JFLAP 7.0 to replace the usage of System.out and System.err by a logger facade (slf4j) plus some code to enhance the current API and to provide command line tools. 

## Installation

This project relies on [jitpack.io](https://jitpack.io/#citiususc/jflap-lib/1.0) instead of maven central to deliver artifacts. If you use maven, just add the following snippet to your `pom.xml` file to use the jitpack repository:

```xml
<repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
</repository>
```

Finally, include jflap-lib as a dependency:

```xml
<dependency>
    <groupId>com.github.citiususc</groupId>
    <artifactId>jflap-lib</artifactId>
    <version>1.0</version>
</dependency>
```

You can also download the compiled jars from the [release page](../../releases) or from [jitpack.io](https://jitpack.io/#citiususc/jflap-lib/1.0).

## Example

It is very easy to use JFLAP programatically. Here is an example of how to load a jff automaton 
and test it with an input:

```java
// Load an automaton jff file
FiniteStateAutomaton automaton = (FiniteStateAutomaton)new XMLCodec().decode(new File("example.jff"), null);
// Load a simulator to test the automaton
AutomatonSimulator sim = SimulatorFactory.getSimulator(automaton);
if (sim == null) throw new RuntimeException("Cannot load an automaton simulator for " + automaton.getClass());
// Test the automaton with an input
System.out.println(sim.simulateInput("10010"));
```

## JFLAP 7.0 License

This project contains the original JFLAP 7.0 source code with some modifications to make it suitable for using it as a library. Here is a copy of the original JFLAP 7.0 License:

    JFLAP 7.0 LICENSE
    
    Susan H. Rodger
    Computer Science Department
    Duke University
    August 27, 2009
    
    Duke University students contributing to JFLAP source include: Thomas Finley,
    Ryan Cavalcante, Stephen Reading, Bart Bressler, Jinghui Lim, Chris Morgan,
    Kyung Min (Jason) Lee, Jonathan Su and Henry Qin.
    
    Copyright (c) 2002-2009
    All rights reserved.
    
    
    I)  You are allowed distribute unmodified copies of JFLAP under the following two conditions:
        1) You must include a copy of this license text.
        2) You cannot charge a fee for any product that includes any part of JFLAP, in source or binary form.
    
    
    II) You are allowed to distribute modified copies of JFLAP under the following conditions:
        1) You must include a copy of this license text.
        2) You cannot charge a fee for any product that includes any part of your modified JFLAP, in source or binary form.
        3) If you made the changes yourself, you must clearly describe how to contact you.
           When the maintainer asks you (in any way) for a copy of the modified JFLAP you distributed, you
           must make your changes, including source code, available to the maintainer without fee.  
           The maintainer reserves the right to include your changes in the official version of JFLAP. 
           The current maintainer is Susan Rodger <jflap@cs.duke.edu>. If this changes, it will be announced at www.jflap.org.
           
    
    The name of the author may not be used to
    endorse or promote products derived from this software without
    specific prior written permission.
    
    THIS SOFTWARE IS PROVIDED ``AS IS'' AND WITHOUT ANY EXPRESS OR
    IMPLIED WARRANTIES, INCLUDING, WITHOUT LIMITATION, THE IMPLIED
    WARRANTIES OF MERCHANTIBILITY AND FITNESS FOR A PARTICULAR PURPOSE.
