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

The same applies to accessing elements in a *List*

**List's apply method**

*List* also has an apply method that accepts an index and returns the element of the list instance at that index, as shown below:

```scala
scala> val list = List('a', "Scala", 10, 3.5)
list: List[Any] = List(a, Scala, 10, 3.5)

scala> list(1)
res5: Any = Scala

scala> list.apply(1)
res6: Any = Scala
```
