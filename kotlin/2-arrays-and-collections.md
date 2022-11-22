## New array
### Using arrayof
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

### Accessing array elements

```kotlin
val x = num.get(0)
num.set(1, 3) // set second element to 3
val x = num[1]
num[2] = 5
```

## collection
### immutable list
```kotlin
val names: List<String> = listOf<String>("john") // or val names = listOf("john")
```
### mutable list
```kotlin
val names = mutableListOf("john")
names.add("renjith")
```

### set
- can't have duplicate
- not ordered
```kotlin

val names = setOf("john",null,"renjith", "john")
```

### map
```kotlin
// fun <K, V> mapOf(vararg pairs: Pair<K, V>): Map<K, V>
val student: MutableMap<String,String> = mutableMapOf<String,String>("name" to "renjith","class" to "10")
student.put("rollno","10")
student["division"] = "A"
```

### iterate
#### list or array 
```kotlin
val names = arrayOf(1,2,3)
for(i in names.indices){ print(names[i]) }

// using range
for (i in 0..names.size-1){ print(names[i]) }
//using foreach
names.forEach({ it -> print(it) })
```
iterate through list after filtering non null items
```kotlin
for(name in mutableListOf("john", null, "renjith").filterNotNull()) {
    print(name)
}
```
#### iterate through map
```kotlin
student.forEach { entry ->
    print("${entry.key} : ${entry.value} \n")
}

// for on iterator
for (entry in map.entries.iterator()) {
    print("${entry.key} : ${entry.value} \n")
}

// iterate over keys
for (key in student.keys) {
    print(key)
}
```

## collection transformation

### Map
```kotlin
val numbers = setOf(1, 2, 3)
print(numbers.map{ it*2}.toString()) // [2, 4, 6]
print(numbers.mapNotNull { if ( it == 2) null else it * 3 }) //[3,9]
print(numbers.mapIndexedNotNull { idx, value -> if (idx == 0) null else value * idx }) //[2, 6]
```
### zip
```kotlin
val colors = listOf("red", "brown", "grey")
val animals = listOf("fox", "bear", "wolf")
// zip in the infix form
println(colors zip animals) // [(red, fox), (brown, bear), (grey, wolf)]

val twoAnimals = listOf("fox", "bear")
println(colors.zip(twoAnimals)) // [(red, fox), (brown, bear)]
```
### unzip
```kotlin
val numberPairs = listOf("one" to 1, "two" to 2, "three" to 3, "four" to 4)
println(numberPairs.unzip()) // returns a Pair ([one, two, three, four], [1, 2, 3, 4])
```
### Associate
```kotlin
val numbers = listOf(1,2,3)
println(numbers.associateWith { it*2 }) //{1=2, 2=4, 3=6}
// gives a map with collection element as key and result of function as value
```

### Flatten
flatten collection of collection
```kotlin
val numberSets = listOf(setOf(1, 2, 3), setOf(4, 5, 6), setOf(1, 2))
println(numberSets.flatten()) //[1, 2, 3, 4, 5, 6, 1, 2]
```
### flatMap
```kotlin
data class Team(
	val members: List<String>
)
val teamA=Team(listOf("one", "two"))
val teamB=Team(listOf("three", "four"))
val all_teams = listOf(teamA,teamB)
println(all_teams.flatMap { it.members }) //[one, two, three, four]
```
### String representation
```kotlin
val numbers = listOf("one", "two", "three")
println(numbers.joinToString("|")) // one|two|three|four
```

## Sequences
Creates a Sequence instance that wraps the original array returning its elements when being iterated.
```kotlin
val numbers = 1 .. 50
val output = numbers.asSequence().filter{
    println("Filtering $it")
    it < 10
}.map{
    println("Mapping $it")
    Pair("Kotlin", it)
}
print(output.toList())
```
