# generic

## function
normal 
```kotlin
fun <T> add(a:T, b:T):T? {
    return when {
    a is Int && b is Int       -> (a.toInt() + b.toInt()) as T
    a is Double && b is Double -> (a.toDouble() + b.toDouble()) as T
    else                       -> null
  }
}
```
extension function
```kotlin
fun <T> List<T>.itemAt(index : Int):T {
    return this[index]
}
```

## generic in class 
```kotlin
class Box<T>(t: T) {
    var value = t
}
//usage
val box: Box<Int> = Box<Int>(1)
val box = Box(1) // compiler decides the type

// T used only in out 
interface Source<out T> {}
```
## Generic constraints
constraints is given after column

### upper bound
```kotlin
fun <T : Comparable<T>> sort(list: List<T>) {  ... }
```
only a subtype of Comparable<T> can be substituted for T

TODO reified and variance