# Nullability
### safe call
```kotlin
m?.method() //call method if m not null
```
### Elvis or null-coalescing operator
```kotlin
newMeeting = m?:Meeting() //new meeting object if m not null
```
### safe cast
```kotlin
val saveable = o as ? | ISaveable //cast to type ISaveable or null
```
### Not-Null assertions
```kotlin
m!!.close() // throw NPE if m is null
```
## Scope Functions
### let
library extension function on any type
Execute a lambda on non-null objects
```kotlin
val len = text?.let {
    print("get length of $it")
    it.length
} ?: 0
```

## extension

```kotlin
fun <class_name>.<method_name>()  
```


## higher order function
A function which can accept a function as parameter or can return a function

```kotlin
// function declaration
val action: (String)->Unit = {x->println("hello "+x)}
// val action = {x: String -> println("hello "+x)}

// higher order function
fun doSomething(myfun: (String) -> Unit){
    myfun("Renjith")
}

// invoke higher order function 
fun main() {
    doSomething(action)
}
```

## Inline and noinline
to reduce the runtime overhead in higher order functions lambda can be inlined.

## object
Object expressions create objects of anonymous classes, that is, classes that aren't explicitly declared with the class declaration
