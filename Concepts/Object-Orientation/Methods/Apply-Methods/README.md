### Apply methods

Methods named *apply* can be invoked by just using parentheses without explicitly calling the method. 
They are also referred to as *default* or *injector* methods.

```scala
scala> class Adder(value: Int) {
     |  def apply(num: Int) = num + value
     | }
defined class Adder

scala> val adder = new Adder(5)
adder: Adder = Adder@1a0d96a5

scala> adder.apply(3)
res3: Int = 8

scala> adder(3)
res4: Int = 8
```

In the above example, the "Adder" class has an *apply* method. 
An instance of type "Adder" is created using which the *apply* method can be called explicitly or implicitly without any method name.

The same applies to accessing elements of a *List*

### Usage in classes and objects

The *apply* method can be used in classes (which implies regular classes) and objects (which implies singleton classes). 

The *apply* method when defined in a class allows any instance of that class to be invoked directly.

For example, consider accessing elements of a *List*

**The *List* class's apply method**

The *List* class has an *apply* method that accepts an index and returns the element of the list instance at that index, as shown below:

```scala
scala> val list = List('a', "Scala", 10, 3.5)
list: List[Any] = List(a, Scala, 10, 3.5)

scala> list(1)
res5: Any = Scala

scala> list.apply(1)
res6: Any = Scala
```

Notice how an instance of the *List* class called "list" is invoked directly by just passing it an index of the element to retrieve without the need to invoke a method directly (as it implicitly invokes the *apply* method).

**The *List* object's apply method**

The *List* object also has an *apply* method which takes arguments and returns a new collection from them. 

```
When an *apply* method is defined in a class, any instance of that class can be invoked directly by just its name followed by necessary arguments.

When an *apply* method is defined in an object, the object can be invoked directly by just its name followed by necessary arguments.
```

