# Futures

A *Future* allows processing the result of a function without waiting for it in the current thread. 
*Futures* allow combining functions asynchronously. 

### History

*Future* type was implemented in

* *Akka* framework, which had its own implementation of the *Future* type
* *scalaz* library
* *Twitter Finagle* library

**Redesigned *scala.concurrent* library to include the *Future* type**

The Scala Improvement Process (SIP-4) recommended the inclusion of the *Future* type in the Scala's standard library with the Scala 2.10 release.
The *scala.concurrent* package was redesigned to include the *Future* type.

### *Futures* vs *Actors*

**Similarities**

*Futures* and *Actors* are asynchronous building blocks that allow for parallel execution.

**Differences**

The building blocks of *Futures* are *asynchronous functions*.

The building blocks of *Actors* are *concurrent objects*.




