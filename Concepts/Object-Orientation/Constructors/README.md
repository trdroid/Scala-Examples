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

### Generating accessor methods

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

scala> person.address_$eq("Milan, Italy")

scala> person.address
res4: String = Milan, Italy
```


