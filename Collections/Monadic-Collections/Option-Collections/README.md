# Option Collections

The *Option* type implies that a single value is either present or absent. It is the type to represent entities that could potentially have no value either because they were not initialized or could not be computed because of an exception or for other similar reasons.

The *Option* type is a monadic collection, the size of which will never be more than one. 

**Purpose**

The purpose of the *Option* type is

* to advertise to the users that the value of an entity in question may not be available, so that it could be used with caution to avoid causing a *NullPointerException*
* to safely build chains of operations and ensure that only valid values persist for the duration of the chain

**Subtypes**

The *Option* type is itself unimplemented but has two subtypes that are implemented.

* Some
* None

*Some* is a type-parameterized collection of cardinality one.

*None* is a collection of cardinality zero.

