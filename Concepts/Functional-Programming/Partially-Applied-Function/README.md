# Partially Applied Function

In functional programming languages, a function is said to be *applied* to the arguments that are passed to the function.

In the following example, the "multiplier" function is said to be *applied* to the arguments 10 & 2.

```scala
scala> val multiplier = (p: Int, q: Int) => p * q
multiplier: (Int, Int) => Int = <function2>

scala> multiplier(10, 2)
res0: Int = 20
```

The output "multiplier: (Int, Int) => Int = <function2>" implies that the function "multiplier" implements the *Function2* trait i.e. it is a function of two parameters.

**Fully applied functions**

A function is said to be *fully applied* to all the arguments, if the function is called with all the required arguments.

In the above example, the "mutiplier" function is said to be *fully applied* to the arguments 10 & 2.

**In contrast**

In contrast, a function is said to be *partially applied*, if it is called with ONLY a subset of the required arguments.  

In the following example, a partial function "partialMultiplier" is created by calling the "multiplier" function with only a subset of the required arguments.

```scala
scala> var partialMultiplier = multiplier(_:Int, 2)
partialMultiplier: Int => Int = <function1>
```

The output "partialMultiplier: Int => Int = <function1>" implies that the partial function "partialMultiplier" implements the *Function1* trait i.e. it accepts only one argument.

The partial function "partialMultiplier" can be called with the remaining arguments.

```scala
scala> val x = partialMultiplier(10)
x: Int = 20
```

