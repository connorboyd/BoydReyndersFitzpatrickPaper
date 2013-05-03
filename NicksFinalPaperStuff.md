#Java 8: Functional Programming implementations

Ever since it's inception, Scala has prided itself on being the best functional programming language on the JVM.
However, Scala may soon become outdated with Java's new update, Java 8.
Java 8 uses what we call "Lambda expressions" to turn the imperative style of programming that is Java into a more functional style.
With the March 2014 updates to the Java language, we may see a complete overtaking of the Scala language with the more widely used, Java implementations.
" *[Java 8] will enable us to write better Java code, using a more 'fluent', functional, and declarative style, with much less boilerplate code for many common use cases* " - Rad Widmer

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
Lambda functions in Java 8 will be closures, rather than regular functions. 
This means that Lambdas do not introduce another level of scope, and can access variables in the enclosing scope. 
This is in contrast to anonymous inner classes, which do introduce a new level of scope.

#Type Inferencing

A useful thing the Lambda expressions will be able to do in Java 8 is type inferencing. 
Type inferencing, initially introduced in the Java 7 sdk, contributes to higher order functional programming. 
This is very useful in programming because we can choose to omit a type definition whenever the compiler could infer that type by itself. 
For example, in this code:

    List<String> list = Arrays.asList(...);
    Collections.sort(list, (s1, s2) -> s1.length() - s2.length());
     
we are able to name arbitrary new variables s1 and s2, but the compiler knows that we are talking about strings so is able to deal with it appropriately. 
The main advantage of Type Inferencing in java 8 is for syntactical sugar. The programmer is essentially limiting the amount needed to type out a function by using type inferencing.
Type inferencing in Java 8 will not be quite as robust as it is in Scala, but it is still a welcome change.

#Streams

One important change in Java 8 to fix this problem will be the addition of Streams; Stream will make transformation operations for collections more simple and efficient.
A Stream is a flow of values created from a data structure that works with higher order functions in Java 8.
Using Streams and higher order functions, it is possible to perform calculations using one statement, whereas using iteration, it would take multiple loops and many more lines of code.
Java collections currently require the creation of temporary variables that hold intermediate steps of the transformation, thus making Java more bulky and slow. 
Streams will eliminate the need for intermediate collection variables/memory and will allow for lazy evaluation. 
On top of this, they will also make the code much easier to read and debug.
Lazy evaluation will further remove bulk from programs by delaying the evaluation of an expression until it is needed. 
Additionally, this avoids repeating the same evaluation, which can reduce run time by an exponential factor. 
This new collection method benefits most on multicore processors by enabling automatic parallelism.

#Parallel Collections

Another update in Java 8 will be to collections. 
With the new lambda expressions, it will be easier to spread out the processing of collections over multiple threads. 
A current problem with Java is that the client code is responsible for processing different elements in parallel. 
With Java 8, the collection will be able to take care of this organization. 
With support for internal iterations of collections, Java will more efficiently utilize parallel hardware. 
This will also help push Java to a more functional programming style, similar to Scala. 

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
These parallel collections will be key to making Java a more competitive functional programming language.

#Conclusion

With these new additions to the Java SDK, Java is moving from an imperative programming language to a more dynamic language that incorporates both imperative and functional programming. 
Scala is purely a functional programming language that uses the JVM, however with the direction Java 8 is moving in, Scala will become less necessary. 
This isn't to say that what we have learned thus far in the course if of no use to us.
On quite the contrary, because the new Java SDK additions are so similar to the functional programming we have been using all semester, every student from the course should, hopefully, be able to pick up Java 8 with relative ease.
Because Java 8 is an update to the already widely popular Java 7 (listed as the most popularly used language on several sites) this means that people who use Java already will be able to experience this new functional type of programming without switching languages.
On top of this, Java 8 will recieve a wide amount of both developer and community support, leading to faster updates and moving towards a more perfect style of functional programming.

---
### Sources ###

 [1] - http://sett.ociweb.com/sett/settFeb2013.html

 [2] - www.infoq.com/articles/java-8-vs-scala

 [3] - http://blog.dhananjaynene.com/2013/02/exploring-java-8-lambdas-part-1/

 [4] - http://cdn.parleys.com/p/5148922b0364bc17fc56c890/1353336439745.pdf

 [5] - http://en.wikipedia.org/wiki/Closure_(computer_science)#Local_classes_.28Java.29

