# if, if/else

The control structures *if* and *if/else* are expressions in Scala. 

The result of an *if* expression is always *Unit*.

The result of an *if/else* expression depends on the type of each part of the expression.

```scala
scala> val a = 2
a: Int = 2

scala> val b = 3
b: Int = 3
```

An *if* expression

```scala
scala> if(a < b) println("true")
true

scala> val q = if (a < b) a*2
q: AnyVal = 4

scala> val x = if(a > b) a*2
x: AnyVal = ()
```

Notice that 'q' and 'x' are resolved to be of type *AnyVal*

```scala
scala> val z: Int = if(a < b) a*2
<console>:13: error: type mismatch;
 found   : Unit
 required: Int
       val z: Int = if(a < b) a*2
                    ^

scala> val z: Int = if(a < b) a*2 else b*2
z: Int = 4
```

Notice that even if a < b, as z is explicitly declared to be an *Int*, the expression "if(a < b) a x 2" cannot be assigned 
to z without have an associated *else*. The reason is without the *else*, the evaluation of *if* could possibly result in a *Unit* type,
which cannot be assigned to 'z' which is declared to be an *Int*. However, with *else*, since both *if* and *else* return an *Int* type, 
the *if/else* expression could be assigned to 'z' directly. 


A multi-line *if* expression

```scala
scala> if(a < b) {
     | println("True")
     | println("a < b")
     | }
True
a < b
```

A multi-line *else*

```scala
scala> val r = if (a < b) a*2 else {
     | val temp = 3
     | b * 2 + temp
     | }
r: Int = 4

scala> val s = if(a > b) a*2 else {
     | val temp = 3
     | b * 2 + temp
     | }
s: Int = 9
```

Using *if/else* as a ternary operator

```scala
scala> val p = if (a < b) a*2 else b*2
p: Int = 4
```
