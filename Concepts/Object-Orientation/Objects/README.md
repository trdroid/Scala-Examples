### Objects

The *object* is a keyword used to define a singleton class in Scala. A singleton class can have no more than one instance. 

An *object* gets automatically instantiated in a running JVM the first time it is accessed.
An *object* is instantiated by directly accessing its name rather than using the *new* keyword.

Using *objects*, Scala provides a clear decoupling between instantiable classes and classes that need not be instantiated. 
An instantiable class needs to be instantiated as its fields and methods are associated with its instances ONLY. A class that needs no instantiation
is a class whose fields and methods can be accessed using the class name without the need for instantiation. 
For example, Java provides the "static" keyword for fields and methods of a class, which can be accessed using the class name without the need to instantiate the class.

An *Object*

* does not take any parameters as they are automatically instantiated
* can extend another class, which makes the class's fields and methods available in a global instance
* cannot be extended
* can contain definitions of fields, methods and internal classes like regular classes.

Methods that are best suited for *Objects* are

1. pure functions

2. methods that deal with external I/O

*Syntax*

```scala
object <identifier> [extends <identifier>] [{ fields, methods, and classes }]
```

```scala
scala> object MyObject {
     |  println("Loading MyObject")
     |  def greet = "Welcome"
     | }
defined object MyObject

scala> println(MyObject.greet)
Loading MyObject
Welcome

scala> println(MyObject.greet)
Welcome
```
