# Traits

A *trait* in Scala can encapsulate field and method definitions. 

**Default Superclass**

The default superclass of a *trait* is *AnyRef*.

Example

Defining a *trait* "MyTrait" encapsulating a method "greet()". "MyTrait" extends from *AnyRef*.

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait
```

### Mix in

A *trait* can be *mixed in* to any number of classes to reuse its fields and methods. 

*Keywords*

A *trait* can be *mixed in* to a class using either

* *extends* keyword
* *with* keyword

**Using *extends* keyword**

A *trait* can be *mixed in* to a class using the *extends* keyword, in which case the class implicitly inherits from the *trait's* superclass.

Example

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait

scala> class MyClass extends MyTrait {
     |  override def toString = "Hello, I am MyClass!"
     | }
defined class MyClass
```

The class "MyClass" mixes in the *trait* "MyTrait" using the *extends* keyword and therefore implicitly inherits from "MyTrait's" superclass *AnyRef*

**Using *with* keyword**

A *trait* can be *mixed in* to a class that explicitly extends from another class by using the *with* keyword.

Example

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait

scala> class A
defined class A

scala> class B extends A with MyTrait {
     |  override def toString = "Hi, I am class B!"
     | }
defined class B
```

Multiple *traits* can be mixed into a class that explicitly extends from another class.

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait

scala> trait AnotherTrait
defined trait AnotherTrait

scala> class P
defined class P

scala> class Q extends P with MyTrait with AnotherTrait
defined class Q
```

### *Trait* as a Type

A variable declared to be of a *Trait* type can reference an instance of any class that *mixes* the *trait*.

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait

scala> class MyClass extends MyTrait {
     |  override def toString = "Hello, I am MyClass!"
     | }
defined class MyClass

scala> val myInstance = new MyClass
myInstance: MyClass = Hello, I am MyClass!

scala> val myTraitRef: MyTrait = myInstance
myTraitRef: MyTrait = Hello, I am MyClass!

scala> myTraitRef.greet()
Hello World!

scala> val myTraitRef1: MyTrait = new MyClass
myTraitRef1: MyTrait = Hello, I am MyClass!

scala> myTraitRef1.greet()
Hello World!
```

### Accessing Members of a Trait

An instance of a class can invoke the methods mixed in from a *trait*.

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait

scala> class MyClass extends MyTrait {
     |  override def toString = "Hello, I am MyClass!"
     | }
defined class MyClass

scala> val myInstance = new MyClass
myInstance: MyClass = Hello, I am MyClass!

scala> myInstance.greet()
Hello World!
```

### Overriding Members of a Trait

```scala
scala> trait MyTrait {
     |  def greet() = {
     |   println("Hello World!")
     |  }
     | }
defined trait MyTrait

scala> val myTraitRef2: MyTrait = new MyKlass
myTraitRef2: MyTrait = Hello, I am MyKlass!

scala> myTraitRef2.greet()
In overridden greet method - Hello, I am MyKlass! Bye.     
```
