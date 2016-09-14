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

### Termination

A *Stream* can be terminated with *Stream.Empty*

**Features**

* A *Stream* is a lazy collection where elements are added to the collection only when accessed for the first time
* A *Stream* is unbounded and can contain infinite elements which are created only upon access
* A *Stream* caches the generated elements so that they are generated only once

