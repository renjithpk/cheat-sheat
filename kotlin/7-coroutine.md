# Coroutines
https://kotlinlang.org/docs/coroutines-basics.html#your-first-coroutine

- Kotlin natively doesn't support coroutines, `kotlinx.coroutines` is the library developed by jetBrains (implementation("org.jetbrains.kotlinx:kotlinxcoroutines-core:1.6.4"))
- A coroutine is an instance of suspendable computation.
- A coroutine is not bound to any particular thread. It may suspend its execution in one thread and resume in another one.
- Coroutines are very lightweight
### Basic Coroutine builders
- `launch` is a coroutine builder. It launches a new coroutine concurrently with the rest of the code, which continues to work independently.
- `runBlocking` is also a coroutine builder that bridges the non-coroutine world of a regular fun main() and the code with coroutines inside of runBlocking { ... }.
- `async` is just like launch, where launch returns a Job and does not carry any resulting value, while async returns a Deferred — a light-weight non-blocking future that represents a promise to provide a result later.
```kotlin
fun main() = runBlocking { // this: CoroutineScope
    launch { // launch a new coroutine and continue
        delay(1000L) // non-blocking delay for 1 second (default time unit is ms)
        println("World!") // print after delay
    }
    println("Hello") // main coroutine continues while a previous one is delayed
    // Structured concurrency -  An outer scope cannot complete until all its children coroutines complete.
    // Here it will be waiting for "World!" to print
}
// ----------- Result ------------
// Hello
// World!
```
`async` example
```kotlin
val time = measureTimeMillis {
    val one = async { doSomethingUsefulOne() } // this will run in parallel with next async
    val two = async { doSomethingUsefulTwo() }
    // `one` and `two` are differed objects, which is also a job. We can cancel if required.
    println("The answer is ${one.await() + two.await()}")
}
// result
// The answer is 42
```

### explicit job
```kotlin
val job = launch {
}
job.join() // wait until child coroutine completes
job.cancel() // cancels the job
job.cancelAndJoin() // cancels the job and waits for its completion
```
## cooperate to allow cancellation
- Option 1: Periodically invoke a suspending function that checks for cancellation. There is a yield function that is a good choice for that purpose.
- Option 2: Explicitly check the cancellation status `while (isActive) { // cancellable computation loop`

### Other functions
- `coroutineScope` Same as runBlocking but, where runBlocking is regular function and coroutineScope is suspending function.
- `withTimeout(1300L) {}` suspending function throws an exception when timeout reached
- `sequence` Sequence type that represents lazily evaluated collections and `yield(value: T)` Yields a value to the Iterator being built and suspends until the next value is requested.
- `yield` Yields the thread (or thread pool) of the current coroutine dispatcher to other coroutines on the same dispatcher to run if possible. `yield(value)` is different which is allowed in only in sequence

