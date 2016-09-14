# Streams

### Generation

A *Stream* is generated from

* one or more starting elements and
* a recursive function

**Similarities with lists**

A *Stream* is a recursive data structure like lists that consists of 

* the current element (the head of a list) - *Base case* and 
* the rest of the collection (the tail of a list) - *Recursive case*

**Stream.cons**

*Stream.cons* can be used to construct a new stream with 

* the current element (the head of a list)
* the rest of the collection specified as a recursive function (the tail of a list)

Example:

The function "doubleNum" returns a *Stream of Int*s which is defined using *Stream.cons* method by passing it 

* its parameter "num", and
* a recursive call to itself by passing in "num + 1"

```scala
scala> def doubleNum(num: Int): Stream[Int] = Stream.cons(num, doubleNum(num + 1))
doubleNum: (num: Int)Stream[Int]

scala> val numStream = doubleNum(1)
numStream: Stream[Int] = Stream(1, ?)

scala> numStream
res5: Stream[Int] = Stream(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, ?)

scala> val numbers = numStream.take(10)
numbers: scala.collection.immutable.Stream[Int] = Stream(1, ?)

scala> val numbersList = numbers.toList
numbersList: List[Int] = List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

scala> val numbersList1 = numStream.take(10).toList
numbersList1: List[Int] = List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

```

### Termination

A *Stream* can be terminated with *Stream.Empty*

**Features**

* A *Stream* is a lazy collection where elements are added to the collection only when accessed for the first time
* A *Stream* is unbounded and can contain infinite elements which are created only upon access
* A *Stream* caches the generated elements so that they are generated only once

