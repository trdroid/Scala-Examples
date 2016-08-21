# Arrays

An array is a collection of data elements of the same type. The elements are associated with an index using which they can be accessed or replaced.

### Declaring an Array

An array of *String*s can be declared in the following ways

Declaration with initilization of array elements, with the type of the array inferred from the type of the elements

```scala
scala> var languages = Array("Scala", "Erlang", "Elixir", "Clojure", "F#")
languages: Array[String] = Array(Scala, Erlang, Elixir, Clojure, F#)
```

Declaration with an explicit mention of the type

```scala
scala> var languages:Array[String] = new Array[String](3)
languages: Array[String] = Array(null, null, null)
```

Declaration with the type inferred

```scala
scala> var languages = new Array[String](3)
languages: Array[String] = Array(null, null, null)
```

### Assigning and Accessing elements

*Assigning*

```scala
scala> var languages = new Array[String](3)
languages: Array[String] = Array(null, null, null)

scala> languages(0)
res0: String = null

scala> languages(1)
res1: String = null

scala> languages(2)
res2: String = null

scala> languages(3)
java.lang.ArrayIndexOutOfBoundsException: 3
  ... 32 elided

scala> languages(0) = "Clojure"

scala> languages(1) = "Elixir"

scala> languages(2) = "F#"

scala> languages
res7: Array[String] = Array(Clojure, Elixir, F#)

scala> languages(0)
res8: String = Clojure

scala> languages(1)
res9: String = Elixir

scala> languages(2)
res10: String = F#

scala> languages(3)
java.lang.ArrayIndexOutOfBoundsException: 3
  ... 32 elided

scala> languages(0)
res12: String = Clojure
```

Notice how every statement in REPL is taking up a 'res' variable implying that every statement in Scala is an expression. Notice the jump from res2 to res7 and res10 to res12.

