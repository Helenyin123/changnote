# Java, C++, Python Basic Knowledge

#### [Difference Between Java and C++](https://www.wikiwand.com/en/Comparison_of_Java_and_C%2B%2B)

| Java | C++ |
| :---: | :---: |
| Platform Independent  | Platform Dependent |
| Run in Java Virtual Machine | Run in Native Executable Machine |
| No pointers |  Have Pointers |
| Support Pass-by-Reference and Pass-by-Value on all types | All types\(primitive & reference\) are passed by value |
| \(Arithmetic, Comparison\) Operators Not Overridable | Support Operator Overloading |
| Automatic Garbage Collection | Manually Memory Management |
| Support Multithreading | Doesn't Support Multithreading |
| No Templates | Support Templates |
| No Global Variables | Have Global Variables |
| Only Single Inheritance of class | Support multiple inheritance of class |

##### What is Platform Independent?

Platform independence means that the same program works on any platform \(operating system\) without any modification.

Some languages are platform independent at the source code level \(C/C++ is a good example\) but lose platform independence once the code is compiled \(since native code is platform specific\). Java retains platform independence even after code is compiled because it compiles to platform independent byte code \(the actual conversion to native code is handled at a later time after the byte code is loaded by the JVM\). The same Java algorithms \(typically compiled to Java byte code and packaged in a .jar file\) will run identically on Windows and Linux.

##### Inheritance

##### Garbage Collection & Memory Management  
Java offers automatic garbage collection, which may be bypassed in specific circumstances via the real time java specification. Memory management in C++ is usually done via constructors, destructors and small pointers. The C++ standard permits garbage collection, but doesn't require it. Garbage collection is rarely used in practice. 





