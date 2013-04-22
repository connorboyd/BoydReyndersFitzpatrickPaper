#Parallel Collections

The name Scala is a blend of the words scalable and language.
Scala was designed to be easily scalable to very large problems.
One key feature that makes this possible is Scala's parallel collections.
In many languages, including Java, utilizing multiple CPU cores is difficult, unintuitive, and cumbersome.
In Scala, scaling up to multiple threads can be as easy as adding one extra keyword to a statement.
An example of this can be seen here:

    def heavyComputation = "abcdefghijk".permutations.size
    (0 to 10).par.foreach(i => heavyComputation)

In this example, heavyComputation is a function that takes a large amount of time to complete.
Performing these computations in parallel would normally be very difficult, but with Scala, adding the par keyword automatically scales the computations to utilize all available cores and dramatically speed up the program.
Java 8 adds nearly identical capabilities with the new parallel collections.
This example demonstrates Java's parallel collections:

    Array.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10).parallel().foreach(int i -> heavyComputation() )

Java's parallel collections are nearly identical to Scala's.
The parallel collections will be key to making Java more competitive with Scala.