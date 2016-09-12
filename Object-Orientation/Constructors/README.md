### Constructors

The entire body of a class constitutes its constructor. The parameters of a constructor are declared immediately after the class name.
If the constructor does not take any parameters, the parameter list can be omitted. 

The following class declaration implies that its constructor takes two parameters

```scala
scala> class Person(val name: String, var address: String)
defined class Person
```

The following class declaration implies that its constructor does not take any parameters.

```scala
scala> class Vehicle
defined class Vehicle
```

### Declaring parameters

The parameters(fields) in the constructor can be declared using the following keywords

* var
* val
* private var
* private val
* or no keyword at all (none of the above).

Constructors are differentiated based on how the parameters are declared.

**Parameters declared as val**

**Parameters declared as var**

**Parameters declared as private val or private var**

When a parameter is declared in the constructor with *private val* or *private var*, its getter(accessor) and setter(mutator) methods are not generated.
It can ONLY be accessed from within the class.

```scala
```

**Parameters declared without var or val**

When a parameter is declared in the constructor without *var* or *val*, its getter(accessor) and setter(mutator) methods are not generated. It CANNOT be accessed even from with in the class. 

```scala
```

**Named parameters**

The parameter names can be used when instantiating an object.

```scala
scala> class Person(val name: String)
defined class Person

scala> val person = new Person
<console>:12: error: not enough arguments for constructor Person: (name: String)Person.
Unspecified value parameter name.
       val person = new Person
                    ^

scala> val person = new Person(name="Jai")
person: Person = Person@b2c5e07

scala> person
res0: Person = Person@b2c5e07
```

```scala
scala> class Person(val name: String) {
     |  override def toString = s"Name:$name"
     | }
defined class Person

scala> val person1 = new Person
<console>:12: error: not enough arguments for constructor Person: (name: String)Person.
Unspecified value parameter name.
       val person1 = new Person
                     ^

scala> val person = new Person(name="Jai")
person: Person = Name:Jai

scala> person
res0: Person = Name:Jai
```

The names of the parameters in the declaration and the instantiation should match.

```scala
scala> class Person(val name: String)
defined class Person

scala> val person = new Person(n="Jai")
<console>:12: error: not found: value n
       val person = new Person(n="Jai")
```

Named parameters can be used only for the preferred parameters.

```scala
scala> class Person(val name: String, val address: String)
defined class Person

scala> val person = new Person(name="Jai", "Tokyo, Japan")
person: Person = Person@135606db

scala> val person1 = new Person("Keith", address="Colombo, Srilanka")
person1: Person = Person@27d5a580

scala> val person2 = new Person(name="John", address="Auckland, New Zealand")
person2: Person = Person@7d898981
```

**Default values for parameters**

The constructor parameters can be provided with default values.

```scala
scala> class Person(val name: String = "Homosapien", val address: String = "Earth") {
     |  override def toString = s"Name:$name, Address:$address"
     | }
defined class Person

scala> val person = new Person
person: Person = Name:Homosapien, Address:Earth

scala> val person1 = new Person("Jai")
person1: Person = Name:Jai, Address:Earth

scala> val person2 = new Person("Jai", "Tokyo, Japan")
person2: Person = Name:Jai, Address:Tokyo, Japan

scala> val person3 = new Person(name = "Jai")
person3: Person = Name:Jai, Address:Earth

scala> val person4 = new Person(address = "Mars")
person4: Person = Name:Homosapien, Address:Mars

scala> val person5 = new Person(address = "Colombo, Srilanka", name = "Jai")
person5: Person = Name:Jai, Address:Colombo, Srilanka

scala> val person6 = new Person(name = "Jai", address = "Melbourne, Australia")
person6: Person = Name:Jai, Address:Melbourne, Australia
```

Note that with named parameters, parameters need not be passed in the order they are declared in the constructor when instantiating an object.

### Examples... Generated accessor, mutator methods

The accessor and mutator methods that are generated for fields depend on how they are declared in the constructor's parameter list. 

```scala
scala> class Person(val name: String, var address: String)
defined class Person
```

For the class "Person" defined above, the following accessor, mutator methods are generated depending on how the member fields are declared in the constructor parameter list.

* a getter (an accessor) method for "name", as it is declared with *val*, which implies a *read-only* (an immutable) member field
* both getter (an accessor) and setter (a mutator) methods for "address", as it is declared with *var*, which implies a *read & write* (a mutable) member field

This can be verified by decompiling the class 

```scala
scala> :javap -c Person
Compiled from "<console>"
public class Person {
  public java.lang.String name();
    Code:
       0: aload_0
       1: getfield      #11                 // Field name:Ljava/lang/String;
       4: areturn

  public java.lang.String address();
    Code:
       0: aload_0
       1: getfield      #15                 // Field address:Ljava/lang/String;
       4: areturn

  public void address_$eq(java.lang.String);
    Code:
       0: aload_0
       1: aload_1
       2: putfield      #15                 // Field address:Ljava/lang/String;
       5: return

  public Person(java.lang.String, java.lang.String);
    Code:
       0: aload_0
       1: aload_1
       2: putfield      #11                 // Field name:Ljava/lang/String;
       5: aload_0
       6: aload_2
       7: putfield      #15                 // Field address:Ljava/lang/String;
      10: aload_0
      11: invokespecial #23                 // Method java/lang/Object."<init>":()V
      14: return
}
```

It can be noticed that the "Person" class has the following generated methods

* a constructor that takes two String arguments, name and address; 
* a getter (an accessor) called "name()" that returns "name", a String; 
* a getter (an accessor) called "address()" and a setter (a mutator) called "address_$eq" for "address"

```scala
scala> val person = new Person("Jai", "London, U.K.");
person: Person = Person@7c75222b

scala> person.name
res0: String = Jai

scala> person.name = "John"
<console>:13: error: reassignment to val
       person.name = "John"
                   ^

scala> person.address
res1: String = London, U.K.

scala> person.address = "Tokyo, Japan"
person.address: String = Tokyo, Japan

scala> person.address
res2: String = Tokyo, Japan

scala> person.address_$eq("Milan, Italy")

scala> person.address
res4: String = Milan, Italy
```

Note that the *val* declaration ONLY prevents a setter from being generated, however its value can be set when instantiating an object.

### Defining more than one constructor

One or more auxiliary constructors for a class can be defined for a class which allows different ways of creating instances for that class. 

Auxiliary constructors

* are defined by creating methods named *this* with non-conflicting signatures.
* Each auxiliary constructor MUST begin by calling a previously defined constructor.

```scala
scala> class Person(val name: String, var address: String) {
     |  def this(name: String) {
     |   this(name, "Earth")
     |  }
     |
     |  def this() {
     |   this("Jai")
     |   this.address = "Colombo, Srilanka"
     |  }
     |
     |  override def toString = s"Name: $name Address: $address"
     | }
defined class Person

scala> val person1 = new Person
person1: Person = Name: Jai Address: Colombo, Srilanka

scala> val person2 = new Person("Keith")
person2: Person = Name: Keith Address: Earth

scala> val person3 = new Person("John", "Seoul, Korea")
person3: Person = Name: John Address: Seoul, Korea
```

