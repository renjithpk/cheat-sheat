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
val mapped = value?.let { transform(it) } ?: defaultValue
```
### run
same as `let` receiver is this instead of lambda arg
```kotlin
val len = text?.run {
    print("get length of $this")
    length // `this.` can be omitted
} ?: 0
```
### apply
The context object is available as a receiver (this). The return value is the object itself.

### also
The context object is available as an argument (it). The return value is the object itself.

### with
A non-extension function: the context object is passed as an argument, but inside the lambda, it's available as a receiver (this). The return value is the lambda result.

## extension

```kotlin
fun <class_name>.<method_name>()  
```
## infix
 - must be member function or extension 
 - single parameter with no default value
```kotlin
infix fun Int.add(b: Int):Int{
    return this + b 
}
print(4 add 5) // 9
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
