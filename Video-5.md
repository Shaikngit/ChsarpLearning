<u>Platform Dependence vs Platform Independence</u>

1. If a program can run only on a specific platform (combination of OS and hardware), it is called Platform Dependent.

Eg:- Cobol, Fortran, C, C++ are Platform Dependent languages 

    Developing an Application using C++ on Windows platform 

    C++ Source Code → Compiled by C++ Compiler → Machine Code(.exe)

         Machine code is the one which is given to customer , Source code is not given to customer. The reason why Source code is not given to customer is, Customer can be charged further for maintenance and enhancements if they don't have source code.

    You can take this machine code .exe file and you can run on any Windows machine without installing C++ compiler or any other tools because machine code is OS understable code. But at the same time you can run this machine code only on Windows platform as it was compiled for Windows platform. 

    This is called Platform Dependent.     


2. If a program can run on multiple platforms without modification, it is called Platform Independent.

All languages before 1995 were Platform Dependent. because they compiled to Machine code which is specific to a particular microprocessor architecture. 

Java introduced the concept of Platform Independence in 1995 by compiling source code to Bytecode, which can run on any platform with a Java Virtual Machine (JVM).

Java, C# , Python are Platform Independent languages because they compile to intermediate code (Bytecode for Java, CIL for C#, Bytecode for Python) which can run on any platform with the respective runtime environment (JVM for Java, .NET runtime for C#, Python interpreter for Python).

    Developing an Application using Java on Windows platform 

    Java Source Code → Compiled by Java Compiler → Byte Code 

    Byte code is not Machine code or OS understandable code. To run the Byte Code client needs to install special software provided by Java known as Java runtime environment (JRE) which has Java Virtual Machine (JVM) inside it. JRE is the one which will convert Byte code to Machine code based on the underlying platform. 

### Java Platform Independence - How JRE/JVM works on different platforms:

**Client 1** → Machine is **Windows** Platform installed with Windows JRE
Byte Code → JVM → Windows Machine Code

**Client 2** → Machine is **Linux** Platform installed with Linux JRE
Byte Code → JVM → Linux Machine Code

**Client 3** → Machine is **Mac** Platform installed with Mac JRE
Byte Code → JVM → Mac Machine Code

**Client 4** → Machine is **Solaris** Platform installed with Solaris JRE
Byte Code → JVM → Solaris Machine Code

> The same Byte Code runs on all platforms because JVM converts it to platform-specific Machine Code at runtime.


