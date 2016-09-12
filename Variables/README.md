# Variables

Variables in Scala can be defined using

* var
* val
* lazy val

A variable declared using *val* is a mutable variable

A variable declared using *val* is an immutable (read-only) variable

Only *val* variables can be additionally declared as *lazy* by declaring them as *lazy val*s. A *lazy val* is calculated ONLY once when it is first accessed. A variable should be declared as a *lazy val* if the cost of calculating it is very long and if it may not be used.


