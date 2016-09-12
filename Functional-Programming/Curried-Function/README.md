# Curried Function

Currying converts a function that accepts mutiple arguments to a chain of functions with each function accepting a single argument.

**Definition & Usage**

Curried functions are defined with the parameter list organized as shown below.

```scala
scala> def curriedMultiplier(p: Int)(q: Int) = p * q
curriedMultiplier: (p: Int)(q: Int)Int

scala> curriedMultiplier(10)(2)
res1: Int = 20
```

The parameter list can also be organized in the following manner.

```scala
scala> def curriedAdder(p: Int) = (q: Int) => p + q
curriedAdder: (p: Int)Int => Int

scala> curriedAdder(10)(2)
res2: Int = 12
```
