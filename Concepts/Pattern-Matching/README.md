### Basics


### Matching Any types

```scala
scala> val list = List("Clojure", 10, 15.9, 'c', "Scala", 20, 3.2)
list: List[Any] = List(Clojure, 10, 15.9, c, Scala, 20, 3.2)

scala> for(element <- list) {
     |  element match {
     |   case strElement: String => println("String:" + strElement)
     |   case intElement: Int => println("Integer:" + intElement)
     |   case doubleElement: Double => println("Double:" + doubleElement)
     |   case other => println("other:" + other)
     |  }
     | }
String:Clojure
Integer:10
Double:15.9
other:c
String:Scala
Integer:20
Double:3.2
```

