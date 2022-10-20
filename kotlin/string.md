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


