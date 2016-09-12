

### Classes and Objects

A class is a blueprint for the objects that can be instantiated from it. 
A class definition consists of field declarations and method definitions.

The fields are used to store the state of an object and are defined either with the keywords *val* or *var*

Method definitions

* provide access to the fields of an object
* perform computations on/using an object's state
* alter the state of an object

Methods are defined with the keyword *def*

An object is a concrete instantiation of the class that it belongs to.

**Defining a class**

```scala
$ scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_91).
Type in expressions for evaluation. Or try :help.

scala> class Person
defined class Person
```

This declaration corresponds to the following class declaration in Java

```java
class Person {
}
```

This can be verified by decompiling the class using the *javap* command.

On Windows,

```scala
scala> :javap
:javap [-lcsvp] [path1 path2 ...]

scala> :javap -c
usage       :javap [opts] [path or class or -]...
-help       Prints this help message
-raw        Don't unmangle REPL names
-app        Show the DelayedInit body of Apps
-fun        Show anonfuns for class or Class#method
-verbose/-v Stack size, number of locals, method args
-private/-p Private classes and members
-package    Package-private classes and members
-protected  Protected classes and members
-public     Public classes and members
-l          Line and local variable tables
-c          Disassembled code
-s          Internal type signatures
-sysinfo    System info of class
-constants  Static final constants

scala> :javap -c Person
Failed: No javap tool available: scala.tools.nsc.interpreter.JavapClass$JavapTool6 failed to initialize.
```

On Ubuntu

```scala
$ scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_65).
Type in expressions for evaluation. Or try :help.

scala> class Person
defined class Person

scala> :javap
:javap [-lcsvp] [path1 path2 ...]

scala> :javap -c
usage       :javap [opts] [path or class or -]...
-help       Prints this help message
-raw        Don't unmangle REPL names
-app        Show the DelayedInit body of Apps
-fun        Show anonfuns for class or Class#method
-verbose/-v Stack size, number of locals, method args
-private/-p Private classes and members
-package    Package-private classes and members
-protected  Protected classes and members
-public     Public classes and members
-l          Line and local variable tables
-c          Disassembled code
-s          Internal type signatures
-sysinfo    System info of class
-constants  Static final constants

scala> :javap -c Person
Compiled from "<console>"
public class Person {
  public Person();
    Code:
       0: aload_0
       1: invokespecial #9                  // Method java/lang/Object."<init>":()V
       4: return
}

scala> 
```

**Creating objects**

Objects of a class can be created with the *new* keyword followed by the name of the class.

```scala
scala> new Person
res0: Person = Person@7d286fb6

scala> new Person()
res1: Person = Person@51133c06
```

