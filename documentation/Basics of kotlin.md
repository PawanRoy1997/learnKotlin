# Basic syntax

Here is a collection of basic syntax elements with example with I took
from [kotlinlang](https://kotlinlang.org/docs/basic-syntax.html) websit.

## Package definitions and imports

Same as in java, the package specification should be at the top of the source file.

```kotlin
package your.project.name

import kotlin.Array
```

## Program entry point

An entry point of a Kotlin application is the main function.
Same as Java, but here is a catch kotlin in statically typed so we don't have to explicitly type public static and
no need to provide args.

```kotlin
fun main() {
    println("Hello World!")
}
```

We can also provide args if we want to, but that is completely optional

```kotlin
fun main(args: Array<String>) {
    print(args.contentToString())
}
```

In kotlin, the datatype are declared on the right side which is opposite to java. We will see more examples of this in
later sections

## Print to the standard output

Unlike java, in kotlin we can use `print` function as it is already imported by default. So, no need to
type `System.out.print("some message")`.
Do it like

```kotlin
print("Hello World")
println("Hello World!")
```

## Functions

We can write function to add two number as

```kotlin
fun sum(num1: Int, num2: Int)Int {
    return num1 + num2
}
```

Kotlin supports higher order function and functional programming paradigm so. We can declare above function as

```kotlin
fun sum(num1: Int, num2: Int): Int = num1 + num2
```

or as

```kotlin 
fun sum(num1: Int, num2: Int) = num1 + num2
```

## Variables

Read-only local variables are defined using keyword `val`. They can be assigned value once.

```kotlin
val num: Int = 1 // Immediate mode of assignment
val num = 1 // Type is inferred as `Int`
val num: Int // Type is required no initialization is provided
num = 1 // Deferred mode of assignment
```

Since, kotlin support functional programming, we can also do

```kotlin
val sum = { num1: Int, num2: Int -> num1 + num2 }
```

## Creating Classes and instances

To define a class, use the `class` keyword.

```kotlin
class Shape
```

Properties of class can be listed in its declaration or body.

```kotlin
class Rectangle(height: Double, length: Double) {
    var perimeter = (height + length) * 2
}
```

The default constructor with parameters listed in the class declaration is available automatically.

```kotlin
val rectangle = Rectangle(5.0, 2.0)
println("The perimeter is ${rectangle.perimeter}")
```

Inheritance between classes is declared by a colon (:). Classes are final by default; to make a class inheritable, mark
it as `open`.

```kotlin
open class Shape

class Rectangle(height: Double, length: Double) : Shape() {
    var perimeter = (height + length) * 2
}
```

## Comments

Just like most modern languages, kotlin supports single-line (or end-line) and multi-line(block) comments.

```kotlin
// This is an end-of-line comment
/* This is a block comment
on multiple lines. */
```

Block comments in Kotlin can be nested.

```kotlin
/* The comment starts here
/* contains a nested comment */
and ends here. */
```

## String templates

```kotlin
var a = 1
// simple name in template:
val s1 = "a is $a"
a = 2
// arbitrary expression in template:
val s2 = "${s1.replace("is", "was")}, but now us $a"
```

## Conditional expressions

```kotlin
fun maxOf(a: Int, b: Int): Int {
    return if (a > b) a else b
}
```

## for loop

```kotlin
val items = listOf("apple"."banana", "kiwifruit")
for (index in items.indices) println("item at $index is ${items[index]}")
```

## while loop

```kotlin
val items = listOf("apple", "banana", "kiwifruit")
var index = 0
while (index < items.size) {
    println("item at $index is ${items[index]}")
    index++
}
```

## Ranges

Check if a number is within a range `in` operator.

```kotlin
val x = 10
val y = 9
if (x in 1..y + 1) println("fits in range")
```

Check if a number is out of range.

```kotlin
val list = listOf("a", "b", "c")
if (-1 !in 0..list.lastIndex) println("-1 is out of range")
if (list.size !in list.indices) println("list size is out of valid list indices range, too")
```

Iterate over a range

```kotlin
for (x in 1..5) print(x)
```

Or over a progression.

```kotlin
for (x in 1..10 step 2) print(x)
println()
for (x in 9 downTo 0 step 3) print(x)
```

## Collections

Iterable over a collections.

```kotlin
for (item in items) println(item)
```

Check if a collection contains an object using `in` operator.

```kotlin
when {
    "orange" in items -> println("juicy")
    "apple" in items -> println("apple is fine too")
}
```

Using lambda expression to filter and map collections:

```kotlin

val fruits = listOf("banana", "avacado", "apple", "kiwifruit")
fruits
    .filter { it.startsWith("a") }
    .sortedBy { it }
    .map(String::uppercase)
    .forEach(::println)
```

## Nullable values and null checks

A reference must be explicitly marked as nullable when `null` value is possible. Nullable type names have `?` at the
end.
Return `null` if `Str` does not hold an integer:

```kotlin
fun parseInt(str: String): Int? {
    // Some logic here
}
```

## Type checks and automatic casts

The `is` operator checks if an expression is an instance of a type. If an immutable local variable or property is checked for a specific type, there's no need to cast it explicitly:

```kotlin
fun getStringLength(obj: Any): Int? {
    if (obj !is String) return null

    // `obj` is automatically cast to `String` in this branch
    return obj.length
}
```
