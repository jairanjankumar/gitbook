# Scala

'Instance of a class' and 'Object' are synonym in java, but not in scala.

Scala object is a special type of class that can have only one instance.(Scala object represents a singleton class, here we don't call class but call them object.)

Scala doesn't support static members like java. A mechanism to define a static method in Scala, one must place them in an object. Generally we use Scala object for utility methods. So they can be called without even instantiating a class.

1. Scala Objects can extend Classes, but an object cannot be extended to create a class or another object.
2. Objects cannot have a public constructor.
3. Object will only be instantiated on their first use. Next time onwards, same instance would be used. (no use, no instance)

Scala doesn't have 'for' loop.. hmmm.. !!! then, what is 'for' loop syntax in Scala..

Scala 'for' loop is just a syntactical sugar for below control abstractions.

```
foreach
map
flatMap
withFilter
```

Constructor in Scala

1.  Default Constructor

    * doesn't take any argument

    ```
    class DefaultConstructor { 
            var variable = 0
        }
    ```
2.  Primary Constructor

    * take some argument

    ```
    class PrimaryConstructor (var var1:Int) { 
            var variable = var1
        }
    ```
3.  Auxiliary Constructor

    * auxiliary constructors are called with 'this'. auxiliary constructor calls to a previously defined primary constructor.

    ```
    class DemoConstructor (var var1:Int, var2:Int, var3:Int){

            //Auxiliary constructors
            def this()= {
                this(1,1,1);
            }
            def this(v1:Int, v2:Int){
                this(v1,v2,1);
            }
    ```

    why do we need 'Auxiliary constructors'

    * Auxiliary constructors gives flexibility to create instance of class with no / fewer arguments than the PrimaryConstructor.

Apply Methods:

Apply method can be added in Class or Object. But they serve the different purposes when added in class and object.

Apply in Object

```
```

Apply in Class

```
scala> class Test{
     | def apply(i : Int){
     | println("print : " + i)
     | }
     | }
defined class Test

scala> val a = new Test
a: Test = Test@6bfaa0a6

scala> a.apply(10)
print : 10

So, because apply method is defined in class, so no need to specify apply here.

scala> a(10)
print : 10
```

![](https://docs.scala-lang.org/resources/images/tour/unified-types-diagram.svg)

Do you know this, Look at the Return type. How they are changes AnyVal, Any, Int, Option\[Int].

Try to relate with above diagram.

```
scala> def comp(i: Int) = if(i > 7) i
comp: (i: Int)AnyVal

scala> def comp(i: Int) = if(i > 7) i else "as"
comp: (i: Int)Any

scala> def comp(i: Int) = if(i > 7) i else i+1
comp: (i: Int)Int

scala> def comp(i: Int) = if(i > 7) Some(i) else i+1
comp: (i: Int)Any

scala> def comp(i: Int) = if(i > 7) Some(i) else None
comp: (i: Int)Option[Int]
```

Option has 2 subclasses- Some and None

```
scala> val j : Option[Int] = None
j: Option[Int] = None

scala> val j : Option[Int] = Some(7)
j: Option[Int] = Some(7)
```

[https://docs.scala-lang.org/overviews/collections/overview.html](https://docs.scala-lang.org/overviews/collections/overview.html)

shows all collections in package`scala.collection`

![](https://docs.scala-lang.org/resources/images/collections.png)

shows all collections in package`scala.collection.immutable`![](https://docs.scala-lang.org/resources/images/collections.immutable.png)

shows all collections in package `scala.collection.mutable`![](https://docs.scala-lang.org/resources/images/collections.mutable.png)

The associativity of an operator is determined by the operator’s last character. Operators ending in a colon ‘:’ are right-associative. All other operators are left-associative.

E.g.

```
scala> object i  {
     | def ~~(j: Int) = 2*j }
defined object i

scala> i ~~ 3
res0: Int = 6

scala> object i  {
     | def ~:(j: Int) = 2*j }
defined object i


Below didn't work, because Operators ending in a colon ‘:’ are right-associative. 
Look at the error message. (~: is not a member of Int)

scala> i ~: 3
<console>:13: error: value ~: is not a member of Int
       i ~: 3
         ^

To make this work, we can write as below:
scala> 3 ~: i
res2: Int = 6

But, if written as below, then above rule doesn't apply.
scala> i.~:(3)
res3: Int = 6
```

Use lift instead of ()

```
scala> val l = List(8,7)
l: List[Int] = List(8, 7)

scala> l.lift(1)
res31: Option[Int] = Some(7)

scala> l.lift(6)
res30: Option[Int] = None

scala> l.lift(6).getOrElse(10)
res29: Int = 10
```

Case classes

Gives you: toString, equals, hashCode, Pattern matching and factory methods

'flatMap' -> to remember the flatMap, apply **map** first then apply **flatten**

```
flatMap examples:
1)
scala> def threeVal(j: Int) = List(j-1, j , j+1)
threeVal: (j: Int)List[Int]

scala> val o = List(3,4,6)
o: List[Int] = List(3, 4, 6)

scala> o.map(threeVal)
res98: List[List[Int]] = List(List(2, 3, 4), List(3, 4, 5), List(5, 6, 7))

scala> o.map(threeVal).flatten
res99: List[Int] = List(2, 3, 4, 3, 4, 5, 5, 6, 7)

scala> o.flatMap(threeVal)
res100: List[Int] = List(2, 3, 4, 3, 4, 5, 5, 6, 7)

2)
scala> val p = Map("India" -> "New Delhi", "Norway" -> "Oslo", "Comoros" -> "Moroni")
p: scala.collection.immutable.Map[String,String] = Map(India -> New Delhi, Norway -> Oslo, Comoros -> Moroni)

scala> val country = List("India","Norway","Sweden")
country: List[String] = List(India, Norway, Sweden)

scala> country.map(c => p.get(c))
res112: List[Option[String]] = List(Some(New Delhi), Some(Oslo), None)

scala> country.map(c => p.get(c)).flatten
res113: List[String] = List(New Delhi, Oslo)

scala> country.flatMap(c => p.get(c))
res114: List[String] = List(New Delhi, Oslo)
```

**Null** -- is a class.

```
abstract final class Null extends AnyRef
Null is - together with scala.Nothing - at the bottom of the Scala type hierarchy.
Null is a subtype of all reference types; its only instance is the null reference. 
Since Null is not a subtype of value types, null is not a member of any such type. 
For instance, it is not possible to assign null to a variable of type scala.Int.
```

**Nothing** -- is a Trait. Its a subtype of everything. But not superclass of anything. There are no instances of Nothing. Nothing has no possible value.

```
final trait Nothing 
extends Any
```

**null** -- Its an instance of Null- Similar to Java null.

**Nil** -- Represents an empty List of anything of zero length.so, It refers to List which has no contents.

```
case object Nil
extends List[Nothing] with Product
The empty list.
```

**None** -- Used to represent a sensible return value. Just to avoid null pointer exception. **Option has 2 subclasses- Some and None**. None signifies no result from the method.

```
Do you know, None extends Option[Nothing]
case object None
extends Option[Nothing]
```

**Unit**– is analogous to a Java method which is declared void. Unit is a subtype of scala.AnyVal. There is only one value of type Unit, ().

A function that doesn't return anything must have the return type Unit. If it were Nothing then the function could not return a result. The only way to exit the function would be by an exception.

```
class Cheatsheet[T](val value : T){
    def --[T2](f: T => T2) = {
    new Cheatsheet(f(value))
  }
}
```

```
Cheatsheet(2) -- {x => x+1} -- {x => x*2 }
```

java.lang.OutOfMemoryError: Java heap space in REPL

```
scala> val w = Source.fromFile("urban.geojson")(Codec.UTF8).getLines().mkString("")
java.lang.OutOfMemoryError: Java heap space
  at java.util.Arrays.copyOf(Arrays.java:3332)
  at java.lang.AbstractStringBuilder.ensureCapacityInternal(AbstractStringBuilder.java:124)
  at java.lang.AbstractStringBuilder.append(AbstractStringBuilder.java:448)
  ...
```

Fixed By:

Starting the Scala REPL with this command to control

```
Jais-MacBook-Pro:~ $ scala -J-Xmx4096m
Welcome to Scala 2.12.3 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_144).
Type in expressions for evaluation. Or try :help.

scala> import scala.io.{Codec, Source}
import scala.io.{Codec, Source}

scala> val w = Source.fromFile("urban.geojson")(Codec.UTF8).getLines().mkString("")
w: String = "{"type": "FeatureCollection","crs": { "type":
....
```

| SCALA VARIANCE TYPE | SYNTAX | DESCRIPTION                                                                                  |
| ------------------- | ------ | -------------------------------------------------------------------------------------------- |
| Covariant           | \[+T]  | If S is subtype of T, then List\[S] is also subtype of List\[T]                              |
| Contravariant       | \[-T]  | If S is subtype of T, then List\[T] is also subtype of List\[S]                              |
| Invariant           | \[T]   | If S is subtype of T, then List\[S] and List\[T] are unrelated.                              |
|                     |        | Note: NOTE:- Here List is just used forsimplicity. It can be any valid Scala Type/class etc. |

ref : [https://docs.scala-lang.org/tour/variances.html](https://docs.scala-lang.org/tour/variances.html)

Another Example: **trait Function1\[-T, +R]** from the Scala standard library. Function1 represents a function with one argument, where the first type parameter T represents the argument type, and the second type parameter R represents the return type. Function1 is contravariant over its argument type, and covariant over its return type.

* S <: T --- S is a subtype of T
  * <: T is an upper bound of the type parameter S, it means that S can be instantiated only to types that conform to T.
* S >: T --- S is a supertype of T, or T is a subtype of S
* S >: T1 <: T2 --- would restrict S any type on the interval between T1 and T2

call scala repl with **-Xprint:typer** option

**combinators** (e.g map)

**transformer** (e.g. =>)

**function composition** (e.g. andThen)

Today I see even scala document has cheatsheet, Good to check the link

[https://docs.scala-lang.org/cheatsheets/index.html](https://docs.scala-lang.org/cheatsheets/index.html)
