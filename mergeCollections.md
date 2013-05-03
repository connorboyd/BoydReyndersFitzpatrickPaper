#Collections

>Maybe change this section to focus more on the actual Streams

Another update in Java 8 will be to collections. 
With the new lambda expressions, it will be easier to spread out the processing of collections over multiple threads. 
A current problem with Java is that it is the client code that is responsible for processing different elements in parallel. 
With Java 8, the collection will be able to take care of this organization. 
With support for internal iterations of collections, Java will more efficiently utilize parallel hardware. 
This also helps push Java to a more functional programming style. 
A new interface called Stream will make transformation operations for collections more simple and efficient. 
Java collections currently require the creation of temporary variables that hold intermediate steps of the transformation, thus making Java more bulky and slow. 
Stream will eliminate the need for intermediate collection variables/memory and it will allow for lazy evaluation. 
This further removes bulk from programs by delaying the evaluation of an expression until it is needed. 
Additionally, lazy evaluation avoids repeating the same evaluation, which can reduce run time by an exponential factor. 
This new collection method benefits most on multicore processors by enabling automatic parallelism.

>These two sections have too much overlap. We need to combine them or something.

..................................................................................................................

#Parallel Collections

The name Scala is a blend of the words scalable and language.
Scala was designed to scale easily to very large problems.
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

..................................................................................................................

#Focuses more on the streams

Another update in Java 8 will be to collections. 

This also helps push Java to a more functional programming style. 

A new interface called Stream will make transformation operations for collections more simple and efficient. 

Java collections currently require the creation of temporary variables that hold intermediate steps of the transformation, thus making Java more bulky and slow. 

Stream will eliminate the need for intermediate collection variables/memory and it will allow for lazy evaluation. 

>Is that true?
It sounds kind of like monads
Maybe we could incorporate that.

This further removes bulk from programs by delaying the evaluation of an expression until it is needed. 

Additionally, lazy evaluation avoids repeating the same evaluation, which can reduce run time by an exponential factor. 


..................................................................................................................

#Focuses more on the Parallelism

With the new lambda expressions, it will be easier to spread out the processing of collections over multiple threads. 

A current problem with Java is that it is the client code that is responsible for processing different elements in parallel. 

With Java 8, the collection will be able to take care of this organization. 

With support for internal iterations of collections, Java will more efficiently utilize parallel hardware. 

This new collection method benefits most on multicore processors by enabling automatic parallelism.

