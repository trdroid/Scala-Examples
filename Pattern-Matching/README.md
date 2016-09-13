# Pattern Matching 

### match clause

```scala
scala> val isStudent = false
isStudent: Boolean = false

scala> isStudent match {
     |  case true => println("Is a student")
     |  case false => println("Is NOT a student")
     | }
Is NOT a student
```

```scala
scala> val isStudent = false
isStudent: Boolean = false

scala> isStudent match {
     |  case false => println("Is NOT a student")
     | }
<console>:13: warning: match may not be exhaustive.
It would fail on the following input: true
       isStudent match {
       ^
Is NOT a student
```

```scala
scala> val isStudent = false
isStudent: Boolean = false

scala> isStudent match {
     |  case true => println("Is a student")
     | }
<console>:13: warning: match may not be exhaustive.
It would fail on the following input: false
       isStudent match {
       ^
scala.MatchError: false (of class java.lang.Boolean)
  ... 34 elided
```


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

