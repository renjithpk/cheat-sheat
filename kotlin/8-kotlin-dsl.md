
## basic dsl syntax 

```kotlin
fun call(block: (String) -> Unit) {
  block('renjith')
}

call { name ->
   println(name)
}
```
## pass a context without additional variable
```kotlin
fun call(block: String.(String) -> Unit) {
  block("$this $name") 
}

call { name ->
   print(this, name) // this will print hello renjith
}
```

## more clean way to invoke with context object

```kotlin
fun call(block: String.(String) -> Unit) {
  "hello".block("$name") 
}

// when code block is last argument we need not call like call({ print(this)})
call { name ->
   print(this, name) // this will print hello renjith
}
```

## extension

```kotlin
fun String.greet(block: (String)-> Unit) {
    block("Hello $this")
}

"Rejith".greet { greeting ->
    println(greeting) // this will print Hello Rejith
}
```

## infix extension 
```kotlin
infix fun String.greet(block: (String)-> Unit) {
    block("Hello $this")
}

// here we are not using . after string
"Rejith" greet { greeting -> 
    println(greeting) // this will print Hello Rejith
}
```
