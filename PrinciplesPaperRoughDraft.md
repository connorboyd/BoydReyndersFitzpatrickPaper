Scala: The an outdated functional language.

Ever since it's conception, Scala has prided itself on being the only functional programming language [false] on the JVM.
However, Scala may soon become outdated with Java's new update, Java 8.
Java 8 uses what we call "Lambda expressions" to turn the imperative style of programming that is Java into a more functional style like Scala.
With the 2014 updates to the Java language, we may see a complete overtaking of the Scala language with the more widely used, and superior, Java implementations.

One of the features of Java 8 that exemplifies functional programming is its use of lambda expressions; these are typically used in GUI development. GUI coding 
is important in connecting events to behaviors. Events can be user actions, such as clicking the mouse or pressing a key. The behavior is the action that 
follows the event. An example of this can be seen using ActionListeners:

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

The ButtonHandler class implements an ActionListener, and stores one method, actionPerformed. ButtonHandler has defined its APIs, declared by ActionListener. 
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

With anonymous inner classes, the new implementation is cleaner, but we still create an instance of a class for a single method. Lambda expressions solve 
these kinds of problems. 
