
C+ Programming Language
=======================

C+ is a project of programming language for educational purposes. The ideas behind this project is to create a similar C language without low level facilities and minimalistic syntax with the power of strong/weak typing and high level abstraction mechanisms.

Some objetives of this language are:   

 - Strong/Weak typing switching
 - Remove all the low level keywords and low level utilities.
 - Add interfaces support and class/module abstraction mechanism.
 - Preserve C ABI interface
 - No scripting, only compiled/binary executables.
 - Standarized mechanisms for serialization/deserialization of data structures. 
 - Have a minimal set of primitive types (value-types and referenced-types).
 - Consistent syntax in order to avoid programmers to write code in different ways to perform same behaviour.  
 - Clear policy of memory management and concurrency facilities.
 - No low-level facilities like pointers and keywords for memory manipulation.
  
Language technology
-------------------   

This language works with a transpiler pair. Does not compile by its own bytecode.   
The decisions behind this are:  

 - Avoid virtual machine design and build compilers from scratch.
 - Take the advantages of compiler optimization from well known languages (C).
 - Open the possibility by translate the language into any language in the future.
 - More easy development for concrete results.


Document
---------------------

(https://docs.google.com/document/d/1heTnD8rZaxwG6Ydp4H3JOvLFNBEqef03qm6FaCPhg1w/edit?usp=sharing)
