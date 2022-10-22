# class


```kotlin
class Person { /*...*/ }
```


## Primary constructor
```kotlin
class Person (firstName: String, var isEmployed: Boolean = true)
```

- constructor keyword required if visibility modifier or annotation is given
```kotlin
class Person constructor(firstName: String) { /*...*/ }
```
- with val/var within the constructor, it declares a property inside the class
```kotlin
open class Shape(val color: String)
// here color doesn't have val/var
class Circle(val radius: Int, color: String): Shape(color)
```
## Initializer blocks

```kotlin
class InitOrderDemo(name: String) {
    init {
        println("Initializer block $name")
    }
}
```
- there can be multiple initializer block which gets executed in the same order 

## Secondary constructor
- each secondary constructor needs to delegate to the primary constructor `:this(name)`
-  initializer are part of primary constructor and gets executed first

```kotlin
class Person(public val name: String) {
    var age: Int = 0
    constructor(name: String, age: Int):this(name) {
        this.age = age
    }
}
```


## Inheritance

```kotlin
open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}

class Circle(radius: String) : Shape() {
    //methods by default open with override
    final override fun draw() { /*...*/ } 
}
```
- classes are final by default (final class means that the class cannot be extended or inherited)

# Abstract classes
- An abstract member does not have an implementation in its class.
- don't need to annotate abstract classes or functions with open
- can override a non-abstract open member with an abstract one.
```kotlin
abstract class Polygon {
    abstract fun draw()
    fun nonAbstract()
}
```
# Interfaces
```kotlin
interface Shape {
    fun show()
}
class Box: Shape {
    override fun show() {
        println("box")
    }
}
fun main() {
    val shape: Shape = Box()
    shape.show()
}
```
- everything public by default
- interface method can have default implementation

## sealed classes
- Sealed class is a class which restricts the class hierarchy
- Constructor is private
- A sealed class cannot be instantiated. Hence, are implicitly abstract.
```kotlin
sealed class Shape{  
    class Circle(var radius: Float): Shape()  
    class Square(var length: Int): Shape()  
}  
  
fun eval(e: Shape) {
    when (e) {  
        is Shape.Circle ->println("Circle area is ${3.14*e.radius*e.radius}")  
        is Shape.Square ->println("Square area is ${e.length*e.length}")  
    }
}
fun main() {
    var circle = Shape.Circle(5.0f)  
    var square = Shape.Square(5) 
    eval(circle)
    eval(square)
}
```
## Data classes

```kotlin
data class User(val name: String, val age: Int)
val jack = User(name = "Jack", age = 1)
// copy with age modified
val olderJack = jack.copy(age = 2)
```
compiler provides :
- equals()/hashCode() pair
- toString() of the form "User(name=John, age=42)"
- componentN() functions corresponding to the properties in their order of declaration.
- copy() function (see below).

## objects
- it can implement interface
- can be derived from classes
- can't have constructor

```kotlin
object School {
    principal: String = "INVALID"
}
School.principal = "new"
```
- Constructor not allowed for objects
- object can be inherited from a class
### nested object
```kotlin
class School {
    object building {
       var count: Int = 10
    }
}
print(School.building.count)
```

## companion object
- to define static methods
- factory object within a class
```kotlin
class Circle(val radius: Int)
class Squire(val side: Int)
class Shape() {
    companion object {
        fun createCircle(arg: Int)= Circle(arg)
        fun createSquire(arg: Int)= Circle(arg)
    }
}

Shape.createCircle(10)
```
