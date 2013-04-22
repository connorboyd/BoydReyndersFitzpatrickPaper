Scala: The an outdated functional language.

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

..................................................................................................................

A useful thing the Lambda expressions will be able to do in Java 8 is type inferencing. 
Type inferencing was initially introduced in the Java 7 sdk, but contribute to higher order functional programming. 
Type inferencing is very useful in programming because we can choose to omit a type definition whenever the compiler could infer that type by itself. 
For example, in this code:

    List<String> list = Arrays.asList(...);
    Collections.sort(list, (s1, s2) -> s1.length() - s2.length());
     
we are able to name arbitrary new variables s1 and s2, but the compiler knows that we are talking about strings so is able to deal with it appropriately. 
The main advantage of Type Inferencing in java 8 is for syntactical sugar. The programmer is essentially limiting the amount needed to type out a function by using type inferencing.

..................................................................................................................

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
