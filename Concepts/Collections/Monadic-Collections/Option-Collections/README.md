### Option Collections

The *Option* type implies that a single value is either present or absent. It is the type to represent entities that could potentially have no value either because they were not initialized or could not be computed because of an exception or for other similar reasons.

The *Option* type is a monadic collection, the size of which will never be more than one. 

The purpose of the *Option* type is

* to advertise to the users that the value of an entity in question may not be available, so that it could be used with caution to avoid causing a *NullPointerException*
* to safely build chains of operations and ensure that only valid values persist for the duration of the chain
