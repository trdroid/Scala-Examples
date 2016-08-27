### Case Classes

A case class has the following properties

* is instantiable
* includes several automatically generated methods by the Scala compiler
* includes an automatically generated companion object with its own automatically generated methods by the Scala compiler

The generated methods in a case class and its associated companion object are based on the class's parameters list. 
The characteristics of some of the methods generated are:

* The *equals* method iteratively compares every field.
* The *toString* method prints the name of the class and all the values of its fields.

**Syntax**

```scala
case class <identifier> ([var] <identifier>: <type>[, ... ])
                        [extends <identifier>(<input parameters>)]
                        [{ fields and methods }]
```

```scala
```
