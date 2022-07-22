# Kotlin

## Types
### Readonly:
```kotlin
val a: Int = 1  // immediate assignment
val b = 2   // `Int` type is inferred
val c: Int  // Type required when no initializer is provided
c = 3       // deferred assignment
```
### Mutable 
```kotlin
var x = 5 // `Int` type is inferred
```
### builtin types
```kotlin
Int
String
Unit
Nothing
Void
```
## Class
- Primary constructor  `Parenthesis after class name`
- Secondary constructor ``


fun main(args: Array<String>)
{
    var a = Add("renjith", "pk")
    println(a.fullname)
    
}
//class with three secondary constructors
class Add(var name:String, lastname: String )
{
    val fullname: String
    init {
        fullname = name + " " +  lastname
    }
}


