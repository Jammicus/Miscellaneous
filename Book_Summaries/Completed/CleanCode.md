# Clean Code Summary  (Robert C. Martin)

-------------------------------------------

[Amazon Link](https://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_1?ie=UTF8&qid=1494149847&sr=8-1&keywords=Clean+code)

-----

## 1. Clean Code

Bad code will bring down a project. Broken window theorem claims that when someone sees bad code in a project, they will undervalue the project and also contribute bad code.

If you see bad code / 'A broken window', fix it.

What is clean code?
	* Elegent
	* Simple
	* Efficient
	* Clear
	* Readable by others
	* Minimal and explicit dependencies
	* Contains Automated tests
	* Minimal classes and methods
	* Demonstrates the ideas of the design
	* Shows that the author cares about the quality of the code.

---------------------------------------------

## 2. Naming

Names should demonstrate the intention of the variable or method, should be pronounceable in human conversation.

Classes should be nouns and variables should be verbs.

When describing a concept, use the same name throughout the project to represent the concept.

	Eg, Representing someone at an auction, consistently call the person a bidder throughout the project, rather than a bidder in some aspects and customer in other aspects, and human in some other aspect.

Refactor bad names to make them clearer if need be.

---------------------------------------------
### 3. Functions

Should do only one thing, and should do it efficiently, should describe what the function does.

Placement of functions in a class should be structured based on how they behave. Functions that call other functions should be placed near the top of the class. With functions that do not call other functions near the bottom.

Parameters should be clear and concise. Should describe what will be passed to the function.

Avoid repeating your functions at all costs.

Think  "Does the name and parameters alone accurately
 describe the function such that another developer could understand without reading the functions body?"

-------------------------------------------

### 4. Comments

Good code will reduce the need for comments. As mentioned above, you're code should be readable to another developer without the need for comments.

However, there are some good scenarios when a comments will be useful:

* Informative comments (Eg, structure of a data type)
* Warnings
* TODOS
* Indicating importance
* Documenting an API

You should try and avoid the following types of comments:

* Comments lacking in clarity
* Change log comments
* Commenting a function rather than splitting it up into sub functions
* Comments that reference non local information

--------------------------------------------------------------------

### 5. Formatting

Classes and files should not be too long. If over 200 lines, think about splitting it up

A good class will be read like an article. It should have the following format:

* A heading
* Key information
* Implementations

Tabs and whitespace should be used for clarity and give the page a good structure.

Try keeping the formatting consistent throughout a project.

-----------------------------------------------------------------

### 6. Objects + Data Structures

Use private variables to keep the internal structure hidden

Try to minimize the number of instance variables

Your base classes should know nothing about the classes that will extend it

Try to use fundamental data structures than inventing your own

Objects should represent one thing

-----------------------------------------------------

### 7. Exception and Error Handling

Try to avoid return codes, instead use exceptions. Your exceptions should be clear and show what type of error has occurred.

When using a try-catch block, think if this happens -> this should be done

---------------------------------------------------------

### 8. Boundaries

Don't pass objects that are often changed around your code.

-----------------

### 9. Unit Tests

Your automated tests should cover all of your codes functionality.

You should do this in a TDD approach (Write the test -> Write the minimal amount of code to pass the test)

Test should be fast and independent of each other

One assert per test

------------------

### 10. Classes

Place your constants first, then variables, then methods.

This applies in methods as well (Constants, variables then method body)

Keep utility methods and all variables private.

Classes should be a small as possible, and should have on responsibility ( Remember S.O.L.I.D)

Class Cohesion = A method that accesses more of the class's variables is more cohesive to the class.  Aim for high cohesion.

----

### 11. Systems.

Always use the simplest thing that can work.

You should follow the Separation of concerns principle. Do not allow convenience to break modularity. (For example, hard coding dependancies is easy, but will break things in the future)

Aim to have full decoupling. This future proofs your work

---

### 12. Emergency.

Remember Kent Becks 4 rules for simple design:

1. Runs all test
2. Contains no duplication
3. Expresses the programmers intent
4. Has only the needed classes and methods (Keep things to a minimal)

-----

### 13. Concurrency

Keep management for concurrency separate from your other code

Limit the access data that your threads will use. Use copies of the data.

Know what will be thread safe/ is not thread safe, blocking/non blocking.

Understand the key concepts of concurrency, deadlocks, mutual exclusion ect...

----

### 14. Successive Refinements

You should be consistently going through you code asking yourself how you can improve / refine it

(The book explains incredibly well how to do this, with examples, I don't feel a summarized version would do it justice)

----

### 15. JUnit Internals

(The book explains incredibly well how to do this, with examples, I don't feel a summarized version would do it justice)

----
### 16. Refactoring

When refactoring, its paramount that what you are refactoring continues to work, and continues to give the expected behaviours

Its a good idea to start at the top of your class / area you want to refactor, and slowly work your way down
---

### 17. Smells and Heuristics

 Smells are things should be not be apparent in your code

* Comments:
	* Inappropriate information
	* Obsolete comments
	* Redundant comments
	* Poor, informative comments
	* Commented-out code
* Environment
	* Having builds that require more than one step (You should not need many steps to build individual elements)
	* Tests that require more than one step
* Functions:
	* Too many arguments (No arguments are best, anything greater than 3 is bad)
	* Output arguments (If your function must change the state of something, have it change the state of the object its called on)
	* Flag arguments (Boolean arguments should be removed)
	* Dead Functions (Any method which is never called should be removed)
* General
	* Multiple languages in one source file
	* Obvious Behavior is Unimplemented (Follow the principle of least surprise - Any function or class should only implement behaviours that another programmer could reasonably expect)
	* Incorrect Behavior at the boundaries - Check boundary conditions, don't rely on your intuition!
	* Overridden Safeties
	* Duplication
	* Code at the wrong level of abstraction - Code should be separated based on their level of abstraction
	* Base classes depending on its derivatives
	* Too much information (Keep it simple!)
	* Dead code (Code that is not executed)
	* Vertical Separation - Functions and variables that are defined far away from where they are used Define local variables above their first usage and put private functions just below their first usage
	* Inconsistency
	* Clutter
	* Artificial Coupling - Things that don't depend on each other should not be artificially coupled
	* Feature envy  - Classes should only be interested in the variables and functions they belong to, not other classes
	* Selector Arguments
	* Obscured Intent - Make the intent of your code visible to your readers
	* Misplaced Responsibility
	* Inappropriate static - Try to use non static methods to static methods. If in doubt, make the function non static.
	* Not using explanatory variables
	* Function names not saying that they do
	* Make sure you understand the algorithm you have written / used
	* Make your local dependencies physical by calling its functions
	* Prefer Polymorphism over IF/else or switch/case
	* Follow standard and language conventions
	* Replace magic numbers with named constants
	* Be  precise
	* Structure over convention
	* Encapsulate your conditionals
	* Avoid negative conditionals (Eg, !buffer.shouldNotCompact())
	* Functions should only do one thing
	* Don't be arbitrary - Have a reason for how you structure your code
	* Encapsulate your boundary conditions - Have variables that represent your boundary conditions
	* Functions should descend only one level of abstraction
	* Keep configurable data at high levels
	* Avoid transitive navigation (Getting one object through another)
* Names:
	* Choose descriptive names
	* Choose names at the appropriate level of abstraction
	* Use convention names where possible
	* Have unambiguous names
	* Use long names for long scopes
	* Avoid encoding
	* Names should describe side effects
* Tests:
	* Insufficient tests
	* Use a coverage tool
	* Don't skip trivial tests
	* Ignored tests is a question about an ambiguity
	* Test boundary conditions
	* Exhaustively test near bugs
	* Patterns of failure are revealing
	* Test coverage patterns can be revealing
	* Tests should be fast
