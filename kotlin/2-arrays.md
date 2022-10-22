## new array
### using arrayof
```kotlin
val num = arrayOf(1, 2, 3, 4)   //implicit type declaration
val num = arrayOf<Int>(1, 2, 3) //explicit type declaration
val num = intArrayOf(1, 2, 3, 4)
```
### Using the Array constructor
```kotlin
val num = Array(3, {i-> i*1})
```
first argument is the size of array and second argument is a lambda function.

### accessing array elements

```kotlin
val x = num.get(0)
num.set(1, 3) // set second element to 3
val x = num[1]
num[2] = 5
```

### traverse

```kotlin
for(i in num.indices){
    println(num[i])
}

// using range
for (i in 0..arrayname.size-1)
{
    println(arrayname[i])
}

//using foreach
arrayname.forEach({ index -> println(index) })

```