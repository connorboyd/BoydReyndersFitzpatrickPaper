Java 8
======

By: Connor Boyd, Doug Fitzpatrick, Nick Reynders

---
### New Features ###

 - Lambdas (closures)
 - Default methods for interfaces
 - Enhanced type inference (target typing)

" *[Java 8] will enable us to write better Java code, using a more 'fluent', functional, and declarative style, with much less boilerplate code for many common use cases* " - Rad Widmer

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

### Streams ###

Primary goals for Java 8:

- modernize the Collections library
- make parallelism easier

But how?

- We use Streams!

---
### Streams Cont. ###

Some key characteristics of a Stream are:

- A Stream has potentially infinite series of values
- A Stream contains no storage for values
- Streams support a functional style of programming
- Streams can be either sequential or parallel 

- The details of how the iteration is performed is controlled by the library.

---
### Obtaining a Stream ###
  - A Stream can also be created given an Iterator or Supplier function (for infinite Streams) 
  - To create a Stream that supports parallel operations, a Spliterator is required 
 - To perform parallel options, a Stream recursively splits the original aggregate into smaller pieces -- each with it's own Spliterator, until a threshold size is reached beyond which any further splitting would just generate additional cost. 
 - The resulting Spliterators can then be iterated over in parallel.

---
### Parallel Processing ###

 - With the new lambda expressions, it will be easier to spread out the processing of collections over multiple threads.

 - Java 8 will more efficiently utilize parallel hardware.

 - This brings Java much closer to Scala in terms of scalability

 - Parallel Streams

		myCollection.parallelStream();

---
### Parallel Processing ###

 - With the new lambda expressions, it will be easier to spread out the processing of collections over multiple threads.

 - Java 8 will more efficiently utilize parallel hardware.

 - This brings Java much closer to Scala in terms of scalability


---
### Parallel Processing ###

	//Lambda
	long sum = myList.stream().filter(i -> i % 2 == 0)
						      .reduce(0L, (a, b) -> a + b);
	
	//Loops
	List<Long> filtered = new LinkedList<Long>();
	for(Long l : myList) {
		if(l % 2 == 0)	{
			filtered.add(l);
		}
	}
	long sum = 0L;
	for(Long l : myList) {
		if(l % 2 == 0)
			sum += l;
	}

- The example using Lambda ran 2.6x faster on average and used all 8 threads on my i7

- The loop example only used 1 thread

- Lambda implementation was also much more concise

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

 - Predicate\<T\>	Returns true if the input matches some criteria

 - Supplier\<T\>		A supplier of objects. The result objects are either created during the invocation of get or by some prior action.

 - Block\<T\>		Performs operations on an object. Can change the state of this object or other objects

 - Function\<T, R\>	Maps an input of type T to an output of type R

 - MultiFunction\<T,U\>	Works similar to "maps" in scala, applies T value to multiple U values

 - BinaryOperator\<T\>	Performs an operation with two operands and returns a result of the same type.

---
### Default Methods ###

 - The main reason for default methods in Java 8 is to support API evolution
 - Adding new methods to an existing interface would break compatibility with older programs which implemented the interface

		public default void forEach(Block<? super T> block)
		public default Predicate<T> negate()


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

 - Both run on JVM
 - Very similar language styles
 - Scala is/has been great preparation for Java 8

---
### Contrasts ###

- in Java 8 a functional interface (with one method) must be declared for EVERY higher order function
- in Scala, no functional interface is needed because functions are 'first class citizens'

---
### Usage ###

 - Java 8 widely used
  - usually listed as most widely used language
 - (should have) more support
 - Java 8 is an update, not an entirely new language

---
### Conclusion ###

- Java 8 will be a powerful new form of functional programming
- supports many features that Scala has
- will be more widely used and thus receive more updates/attention
 - Java 8 is an update
- Java 8 release date is approximately March, 2014

---
### Sources ###

 [1] - http://sett.ociweb.com/sett/settFeb2013.html

 [2] - www.infoq.com/articles/java-8-vs-scala

 [3] - http://blog.dhananjaynene.com/2013/02/exploring-java-8-lambdas-part-1/

 [4] - cdn.parleys.com/p/5148922b0364bc17fc56c890/1353336439745.pdf
