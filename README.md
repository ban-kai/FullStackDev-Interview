# Java Interview Questions Compilation

## 1. Explain JVM, JRE and JDK?

__JVM (Java Virtual Machine)__: It is an abstract machine. It is a specification that provides run-time environment in which java bytecode can be executed. It follows three notations:

* Specification: It is a document that describes the implementation of the Java virtual machine. It is provided by Sun and other companies.
* Implementation: It is a program that meets the requirements of JVM specification.
* Runtime Instance: An instance of JVM is created whenever you write a java command on the command prompt and run the class.

__JRE (Java Runtime Environment)__ : JRE refers to a runtime environment in which java bytecode can be executed. It implements the JVM (Java Virtual Machine) and provides all the class libraries and other support files that JVM uses at runtime. So JRE is a software package that contains what is required to run a Java program. Basically, it’s an implementation of the JVM which physically exists. 

__JDK(Java Development Kit)__ : It is the tool necessary to compile, document and package Java programs. The JDK completely includes JRE which contains tools for Java programmers. The Java Development Kit is provided free of charge. Along with JRE, it includes an interpreter/loader, a compiler (javac), an archiver (jar), a documentation generator (javadoc) and other tools needed in Java development. In short, it contains JRE + development tools.

Refer to this below image and understand how exactly these components reside: ![java](https://cdn-images-1.medium.com/max/1600/0*MsGzRuN1Q09dOkwi.png)

## 2. Is Java a Compiled or an Interpreted programming language ?

Java implementations typically use a two-step compilation process. Java source code is compiled down to bytecode by the Java compiler. The bytecode is executed by a Java Virtual Machine (JVM). Modern JVMs use a technique called Just-in-Time (JIT) compilation to compile the bytecode to native instructions understood by hardware CPU on the fly at runtime.

Some implementations of JVM may choose to interpret the bytecode instead of JIT compiling it to machine code, and running it directly. While this is still considered an "interpreter," It's quite different from interpreters that read and execute the high level source code (i.e. in this case, Java source code is not interpreted directly, the bytecode, output of Java compiler, is.)

It is technically possible to compile Java down to native code ahead-of-time and run the resulting binary. It is also possible to interpret the Java code directly.

At run time, JVM interprets the byte code and executes them. However, a full interpreter based execution potentially hurts the performance of application since pretty much everything that a compiler could have done upfront at compile time will now be done repeatedly by the interpreter and this adds to the overall execution time of the program.

To summarize, depending on the execution environment, bytecode can be:

* compiled ahead of time and executed as native code (similar to most C++ compilers)
* compiled just-in-time and executed
* interpreted
* directly executed by a supported processor (bytecode is the native instruction set of some CPUs)

![java](http://novtopro.qiniudn.com/blog/2017/01/21/kotlin-kickstart/jit.png)

## 3. Why java is not 100% Object-oriented?

Java is not 100% Object-oriented because it makes use of eight primitive datatypes such as boolean, byte, char, int, float, double, long, short which are not objects.

## 4. What are wrapper classes?

Wrapper classes converts the java primitives into the reference types (objects). Every primitive data type has a class dedicated to it. These are known as wrapper classes because they “wrap” the primitive data type into an object of that class. Refer to the below image which displays different primitive type, wrapper class and constructor argument. 

## 5. What is singleton class and how can we make a class singleton?

Singleton class is a class whose only one instance can be created at any given time, in one JVM. A class can be made singleton by making its constructor private.

```java
// Java program implementing Singleton class
// with getInstance() method
class Singleton
{
    // static variable single_instance of type Singleton
    private static Singleton single_instance = null;
 
    // variable of type String
    public String s;
 
    // private constructor restricted to this class itself
    private Singleton()
    {
        s = "Hello I am a string part of Singleton class";
    }
 
    // static method to create instance of Singleton class
    public static Singleton getInstance()
    {
        if (single_instance == null)
            single_instance = new Singleton();
 
        return single_instance;
    }
}
```

## 6. 


Easy ones but worth mentioing: 

* Explain public static void main(String args[])
* Why Java is platform independent?
* What are constructors in Java?
* 