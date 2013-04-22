#Scala: The an outdated functional language.

Ever since it's inception, Scala has prided itself on being the only functional programming language [100% false] on the JVM.
However, Scala may soon become outdated with Java's new update, Java 8.
Java 8 uses what we call "Lambda expressions" to turn the imperative style of programming that is Java into a more functional style like Scala.
With the 2014 updates to the Java language, we may see a complete overtaking of the Scala language with the more widely used, and superior, Java implementations.

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

----------------
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