# Kotlin Unfinished 

## Types
### Numbers

```kotlin
Byte // 1 byte
Short // 4 bytes
Int // 8 bytes, this is usual default
Long // 16 bytes

// floating point
Float // 
Double // default is double
``` 
### Characters
```kotlin
val myGrade: Char = 'B'
//val myLetter: Char = 66  -> Error : can't assign integer
```
### Booleans
```kotlin
val isKotlinFun: Boolean = true
```
### Strings
```kotlin
val myText: String = "Hello World"
val s = "abc" + 1 // abc1 
```
### Arrays
```
val cars = arrayOf("Volvo", "BMW", "Ford", "Mazda")
println(cars[0])
cars[0] = "Opel"
println(cars.size)
if ("Volvo" in cars) {
```

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


