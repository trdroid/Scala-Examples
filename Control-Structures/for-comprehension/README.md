### for comprehension or for expression

The term *comprehension* is inherited from functional programming which implies comprehending elements of one or more collections and computing new elements to generate new collections.

A *for comprehension* allows

* traversing through one or more collections to "comprehend" their elements
* allows elements to be optionally passed through filters
* new values to be computed from the elements/filtered elements
* generation of new collections with the new values computed as elements

**for loops**

*for loops* are *for comprehensions* that do not return anything, but only performs side effects. 
These are analagous to *for loops* in languages like Java.

```scala
scala> val languages = List("Scala", "Java", "Swift", "Clojure", "F#")
languages: List[String] = List(Scala, Java, Swift, Clojure, F#)

scala> for(language <- languages)
     |  println(language)
Scala
Java
Swift
Clojure
F#
```

```scala
scala> val languages = List("Scala", "Java", "Swift", "Clojure", "F#")
languages: List[String] = List(Scala, Java, Swift, Clojure, F#)

scala> :t res0
<console>:12: error: not found: value res0
       res0
       ^

scala> for(language <- languages)
     |  println(language)
Scala
Java
Swift
Clojure
F#

scala> :t res0
Unit
```

### Filters/Guards

*if* expressions can be added to *for comprehensions* to apply filters to a collection. This allows selective processing of elements of a collection.
These expressions are called *filters* or *guards*. 

```scala
scala> for(language <- languages
     |  if language.contains("Clojure"))
     |  println(language)
Clojure

scala> :t res1
Unit
```

**More than one guard**

A *for comprehension* can have more than one guard expression.

```scala
scala> for(language <- languages
     |  if language.contains("Clojure")
     |  if !language.endsWith("ala")
     | ) println(language)
Clojure

scala> :t res2
Unit
```

```scala
scala> for(language <- languages
     |  if language.contains("Clojure") && !language.endsWith("ala")
     | ) println(language)
Clojure

scala> :t res3
Unit
```

