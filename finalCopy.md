#Scala: an outdated functional language.

Ever since it's inception, Scala has prided itself on being the best functional programming language on the JVM.
However, Scala may soon become outdated with Java's new update, Java 8.
Java 8 uses what we call "Lambda expressions" to turn the imperative style of programming that is Java into a more functional style like Scala.
With the 2014 updates to the Java language, we may see a complete overtaking of the Scala language with the more widely used, and superior, Java implementations.

..................................................................................................................

#Lambda Expressions

One of the features of Java 8 that exemplifies functional programming is its use of lambda expressions; these are typically used in GUI development.
GUI coding is important in connecting events to behaviors.
Events can be user actions, such as clicking the mouse or pressing a key.
The behavior is the action that follows the event.
An example of this can be seen using ActionListeners:

    class ButtonHandler implements ActionListener {
          public void actionPerformed(ActionEvent e) {
                //do something
          }
    }

    class UIBuilder {
          public UIBuilder() {
                button.addActionListener(new ButtonHandler());
          }
    }

The ButtonHandler class implements an ActionListener, and stores one method, actionPerformed.
ButtonHandler has defined its APIs, declared by ActionListener. 
This code can be simplified with anonymous inner classes:

>Is this the Lambda example? It's not very clear, and it doesn't look like the other Lambda syntax

>Ok, so I did some reading on anonymous inner classes, and apparently they're not related to Lambdas.
We need to get an example that uses Lambdas.
That's kind of the point of the paper.

    class UIBuilder {
          public UIBuilder() {
                button.addActionListener(new ActionListener() {
                      public void actionPerformed(ActionEvent event) {
                            //do something
                      }
                }
          }
    }

With anonymous inner classes, the new implementation is cleaner, but we still create an instance of a class for a single method.
Lambda expressions solve these kinds of problems. 

>Stuff below is new

Lambda functions in Java 8 will be closures, rather than regular functions. This means that Lambdas do not introduce another level of scope, and can access variables in the enclosing scope.
This contrasts with anonymous inner classes, which do introduce a new level of scope.


..................................................................................................................

#Type Inferencing

A useful thing the Lambda expressions will be able to do in Java 8 is type inferencing. 

>Type inferencing was initially introduced in the Java 7 sdk, but contribute to higher order functional programming. 

>That sentence doesn't make sense

Type inferencing is very useful in programming because we can choose to omit a type definition whenever the compiler could infer that type by itself. 
For example, in this code:

    List<String> list = Arrays.asList(...);
    Collections.sort(list, (s1, s2) -> s1.length() - s2.length());
     
We are able to name arbitrary new variables s1 and s2, but the compiler knows that we are talking about strings so is able to deal with it appropriately. 
The main advantage of Type Inferencing in java 8 is for syntactical sugar. The programmer is essentially limiting the amount needed to type out a function by using type inferencing.

>New stuff below

Type inferencing in Java 8 will not be quite as robust as it is in Scala, but it is still a welcome change

..................................................................................................................

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

#Conclusion

>With these new additions to the Java SDK, Java is moving from an imperative programming language to a more dynamic language that incorporates both imperative and functional programming. 

>Java is not a dynamic language. Dynamic language is something completely different.

Scala is purely a functional programming language that uses the JVM, however with the direction Java 8 is moving in, Scala will become less necessary. 
Java is a more popular language with greater developer support and will therefore be able to update faster continue its move towards functional programming.
