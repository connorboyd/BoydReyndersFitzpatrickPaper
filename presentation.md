Java 8
======

By: Connor Boyd, Doug Fitzpatrick, Nick Reynders

---
### New Features ###

 - Lambdas (closures)
 - Default methods for interfaces
 - Enhanced type inference (target typing)

"`[Java 8] will enable us to write better Java code, using a more 'fluent', functional, and declarative style, with much less boilerplate code for many common use cases`" - Rad Widmer

---
### Lambda Expressions ###

 - Lambda Expressions are Closures
 - New lambda expressions make code prettier and easier to read.

Compare:

		Runnable r = () -> System.out.println("hello world");
		r.run();  // prints "hello world"

with

		Runnable r = new Runnable() {
            	    @Override
            	    public void run() {
                        System.out.println("hello world");
            	    }
        	};
---
### Lambda Expressions Cont.###
	
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


	class UIBuilder {
      		public UIBuilder() {
            		button.addActionListener(new ActionListener() {
                  		public void actionPerformed(ActionEvent event) {
                        	//do something
                  		}
            		}
      		}
	}



---
### Parallel Processing ###

 - With the new lambda expressions, it will be easier to spread out the processing of collections over multiple threads.

 - Java 8 will more efficiently utilize parallel hardware.
 - This brings Java much closer to Scala in terms of scalability


---
### Variable Capture ###

 - A lambda expression may reference variables which are visible in the current scope -- this is what makes lambdas closures instead of simply functions.

 - In contrast to anonymous inner classes, lambdas don't introduce another level of scope.

---
### Shadowing ###

 - Lambda's parameter names can't shadow any local variable names in the enclosing method. The following example would not compile.

		String a, b;

	        List<String> strings = ...;
		// compile error -- lambda parameter names shadow local variables
		strings.sort((a, b) -> a.compareTo(b));
---
### Functional Interfaces ###

##### Some new functions #####

 - Predicate<T>		returns true if the input matches some criteria

 - Supplier<T>		A supplier of objects. The result objects are either created during the invocation of get or by some prior action.

 - Block<T>		Performs operations on an object. Can change the state of this object or other objects

 - Function<T, R>	Maps an input of type T to an output of type R

 - MultiFunction<T,U>	Works similar to "maps" in scala, applies T value to multiple U values

 - BinaryOperator<T>	Performs an operation with two operands and returns a result of the same type.
---
### Default Methods ###






---
### Scala Preparation ###

 - Scala features
	- parallelism
	- closures
	- lambda expressions

 - Java 8 features
	- parallelism
	- closures
	- lambda expressions

 - Very similar language styles
 - Scala is a great preparation for Java 8

---
### Contrasts ###

- in Java 8 a functional interface (with one method) must be declared for EVERY higher order function
- in Scala, no functional interface is needed because functions are 'first class citizens'

---
### Usage ###

 - Java 8 will be more widely used
 - Java 8 will therefore have more support

---
### Conclusion ###

- Java 8 will be a powerful new form of functional programming
- supports many features that Scala has
- will be more widely used and thus receive more updates/attention
- java 8 has been pushed back another year (to 2014)

---
### Sources ###

 [1] - http://sett.ociweb.com/sett/settFeb2013.html

 [2] - www.infoq.com/articles/java-8-vs-scala

 [3] - http://blog.dhananjaynene.com/2013/02/exploring-java-8-lambdas-part-1/

 [4] - cdn.parleys.com/p/5148922b0364bc17fc56c890/1353336439745.pdf