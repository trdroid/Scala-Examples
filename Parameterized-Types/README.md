# Parameterized Types

**Types of Variance under Inheritance**

The types of variance under inheritance are

* Covariance
* Contravariant
* Invariant
* Mixed

**Covariant**

A parameterized type/container is *covariant* if the supertype-subtype relationship of the parameterized type/container "aligns in direction" with the relationship between the type parameters.

Given that A is a super-type of B, if List[A] is a *super-type* of List[B], then this kind of variance is called *covariance*.

Example

```scala
class MyClass[+A] {...}
```

+A is referred to as a *covariant type parameter*

**Contravariant**

A parameterized type/container is *contravariant* if the supertype-subtype relationship of the parameterized type/container "aligns in an opposite direction" with the relationship between the type parameters.

Given that A is a super-type of B, if List[A] is a *sub-type* of List[B], then this kind of variance is called *Contravarience*.

Example

```scala
class MyClass[-A] {...}
```
-A is referred to as a *contravariant type parameter*

**Invariant**

A parameterized type/container is an *invariant* if it is neither a *covariant* nor a *contravariant*.

```scala
class MyClass[A] {...}
```

A is referred to as an *invariant type parameter*

**Mixed**

A parameterized type/container can contain a mix of any type of the aforementioned variants

```scala
class MyClass[+A, -B, C] {...}
```






