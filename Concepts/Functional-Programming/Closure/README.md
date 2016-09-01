# Closure

A *closure* is a function that has visibility of one or more variables defined outside of the function.

Consider defining a function "adder" that references a variable "p" defined outside the function in the enclosing scope.
The following results in an error as the variable "'P is not defined yet.

```scala
scala> val adder = (q: Int) => p + q
<console>:11: error: not found: value p
       val adder = (q: Int) => p + q
                               ^
```

Consider defining "p" as a variable so it can be changed later.

```scala
scala> var p = 5
p: Int = 5

scala> val adder = (q: Int) => p + q
adder: Int => Int = <function1>
```

Notice how the function "adder" references the variable "p" defined in the enclosing scope and adds it with the formal parameter "q" and returns the result.

```scala
scala> adder(2)
res0: Int = 7

scala> adder(10)
res1: Int = 15
```

Consider changing the value of "p" and notice that calling adder now uses the new value of "p"

```scala
scala> p = 10
p: Int = 10

scala> adder(15)
res2: Int = 25
```
