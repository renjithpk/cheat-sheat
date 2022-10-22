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
Unit // void in java
Nothing
// no value, return nothing if control never 
// can reach to return, always exception or infinite loop

Void // from java, not used in kotlin
```
### Strings
```kotlin
val myText: String = "Hello World"
val s = "abc" + 1 // abc1 
```
## escaped string 
`val s = "Hello, world!\n"`

## raw string
```kotlin
val text = """
    for (c in "foo")
        print(c)
"""
```
to remove leading white space
```kotlin
val text = """
    |Tell me and I forget.
    |Teach me and I remember.
    """.trimMargin()
```
## string template
```kotlin
val s = "abc"
println("$s.length is ${s.length}") // Prints "abc.length is 3"
```
This works in raw string as well
- length of string `variable_name.length`

## loop through character
```kotlin
for (c in str) {
    println(c)
}
``` 
### Arrays
```
val cars = arrayOf("Volvo", "BMW", "Ford", "Mazda")
println(cars[0])
cars[0] = "Opel"
println(cars.size)
if ("Volvo" in cars) {
```



