### Case Classes

A case class has the following properties

* is instantiable
* includes several automatically generated methods by the Scala compiler
* includes an automatically generated companion object with its own automatically generated methods by the Scala compiler

The generated methods in a case class and its associated companion object are based on the class's parameters list. 
The characteristics of some of the methods generated are:

* The *equals* method iteratively compares every field.
* The *toString* method prints the name of the class and all the values of its fields.

**Syntax**

```scala
case class <identifier> ([var] <identifier>: <type>[, ... ])
                        [extends <identifier>(<input parameters>)]
                        [{ fields and methods }]
```

```scala
scala> case class Person(name: String, isStudent: Boolean)
defined class Person

scala> :javap -c Person
Compiled from "<console>"
public class Person implements scala.Product,scala.Serializable {
  public java.lang.String name();
    Code:
       0: aload_0
       1: getfield      #16                 // Field name:Ljava/lang/String;
       4: areturn

  public boolean isStudent();
    Code:
       0: aload_0
       1: getfield      #21                 // Field isStudent:Z
       4: ireturn

  public Person copy(java.lang.String, boolean);
    Code:
       0: new           #2                  // class Person
       3: dup
       4: aload_1
       5: iload_2
       6: invokespecial #27                 // Method "<init>":(Ljava/lang/String;Z)V
       9: areturn

  public java.lang.String copy$default$1();
    Code:
       0: aload_0
       1: invokevirtual #30                 // Method name:()Ljava/lang/String;
       4: areturn

  public boolean copy$default$2();
    Code:
       0: aload_0
       1: invokevirtual #33                 // Method isStudent:()Z
       4: ireturn

  public java.lang.String productPrefix();
    Code:
       0: ldc           #36                 // String Person
       2: areturn

  public int productArity();
    Code:
       0: iconst_2
       1: ireturn

  public java.lang.Object productElement(int);
    Code:
       0: iload_1
       1: istore_2
       2: iload_2
       3: tableswitch   { // 0 to 1
                     0: 49
                     1: 39
               default: 24
          }
      24: new           #42                 // class java/lang/IndexOutOfBoundsException
      27: dup
      28: iload_1
      29: invokestatic  #48                 // Method scala/runtime/BoxesRunTime.boxToInteger:(I)Ljava/lang/Integer;
      32: invokevirtual #51                 // Method java/lang/Object.toString:()Ljava/lang/String;
      35: invokespecial #54                 // Method java/lang/IndexOutOfBoundsException."<init>":(Ljava/lang/String;)V
      38: athrow
      39: aload_0
      40: invokevirtual #33                 // Method isStudent:()Z
      43: invokestatic  #58                 // Method scala/runtime/BoxesRunTime.boxToBoolean:(Z)Ljava/lang/Boolean;
      46: goto          53
      49: aload_0
      50: invokevirtual #30                 // Method name:()Ljava/lang/String;
      53: areturn

  public scala.collection.Iterator<java.lang.Object> productIterator();
    Code:
       0: getstatic     #68                 // Field scala/runtime/ScalaRunTime$.MODULE$:Lscala/runtime/ScalaRunTime$;
       3: aload_0
       4: invokevirtual #72                 // Method scala/runtime/ScalaRunTime$.typedProductIterator:(Lscala/Product;)Lscala/collection/Iterator;
       7: areturn

  public boolean canEqual(java.lang.Object);
    Code:
       0: aload_1
       1: instanceof    #2                  // class Person
       4: ireturn

  public int hashCode();
    Code:
       0: ldc           #77                 // int -889275714
       2: istore_1
       3: iload_1
       4: aload_0
       5: invokevirtual #30                 // Method name:()Ljava/lang/String;
       8: invokestatic  #83                 // Method scala/runtime/Statics.anyHash:(Ljava/lang/Object;)I
      11: invokestatic  #87                 // Method scala/runtime/Statics.mix:(II)I
      14: istore_1
      15: iload_1
      16: aload_0
      17: invokevirtual #33                 // Method isStudent:()Z
      20: ifeq          29
      23: sipush        1231
      26: goto          32
      29: sipush        1237
      32: invokestatic  #87                 // Method scala/runtime/Statics.mix:(II)I
      35: istore_1
      36: iload_1
      37: iconst_2
      38: invokestatic  #90                 // Method scala/runtime/Statics.finalizeHash:(II)I
      41: ireturn

  public java.lang.String toString();
    Code:
       0: getstatic     #68                 // Field scala/runtime/ScalaRunTime$.MODULE$:Lscala/runtime/ScalaRunTime$;
       3: aload_0
       4: invokevirtual #94                 // Method scala/runtime/ScalaRunTime$._toString:(Lscala/Product;)Ljava/lang/String;
       7: areturn

  public boolean equals(java.lang.Object);
    Code:
       0: aload_0
       1: aload_1
       2: if_acmpeq     92
       5: aload_1
       6: astore_2
       7: aload_2
       8: instanceof    #2                  // class Person
      11: ifeq          19
      14: iconst_1
      15: istore_3
      16: goto          21
      19: iconst_0
      20: istore_3
      21: iload_3
      22: ifeq          96
      25: aload_1
      26: checkcast     #2                  // class Person
      29: astore        4
      31: aload_0
      32: invokevirtual #30                 // Method name:()Ljava/lang/String;
      35: aload         4
      37: invokevirtual #30                 // Method name:()Ljava/lang/String;
      40: astore        5
      42: dup
      43: ifnonnull     55
      46: pop
      47: aload         5
      49: ifnull        63
      52: goto          88
      55: aload         5
      57: invokevirtual #97                 // Method java/lang/Object.equals:(Ljava/lang/Object;)Z
      60: ifeq          88
      63: aload_0
      64: invokevirtual #33                 // Method isStudent:()Z
      67: aload         4
      69: invokevirtual #33                 // Method isStudent:()Z
      72: if_icmpne     88
      75: aload         4
      77: aload_0
      78: invokevirtual #99                 // Method canEqual:(Ljava/lang/Object;)Z
      81: ifeq          88
      84: iconst_1
      85: goto          89
      88: iconst_0
      89: ifeq          96
      92: iconst_1
      93: goto          97
      96: iconst_0
      97: ireturn

  public Person(java.lang.String, boolean);
    Code:
       0: aload_0
       1: aload_1
       2: putfield      #16                 // Field name:Ljava/lang/String;
       5: aload_0
       6: iload_2
       7: putfield      #21                 // Field isStudent:Z
      10: aload_0
      11: invokespecial #104                // Method java/lang/Object."<init>":()V
      14: aload_0
      15: invokestatic  #110                // Method scala/Product$class.$init$:(Lscala/Product;)V
      18: return
}


```
