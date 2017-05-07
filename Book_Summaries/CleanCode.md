# Clean Code Summary  (Robert C. Martin)

-------------------------------------------

[Amazon Link](https://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_1?ie=UTF8&qid=1494149847&sr=8-1&keywords=Clean+code)

-----

## 1. Clean Code

Bad code will bring down a project. Broken window theorem claims that when someone sees bad code in a project, they will undervalue the project and also contirbute bad code. 

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

Names should demonstrate the intention of the variable or method, should be pronoucable in human conversation.

Classes should be nouns and variables should be verbs.

When describing a concept, use the same name throughout the project to represent the concept. 

	Eg, Representing someone at an auction, consisently call the perosn a bidder throughout the project, rather than a bidder in some aspects and customer in other aspects, and human in some other aspect.

Refactor bad names to make them clearer if need be.

---------------------------------------------
### 3. Functions

Should do only one thing, and should do it efficently, should describe what the function does.

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

You should try and avoid the following types of coments:
	* Comments lacking in clarity
	* Changelog comments
	* Commenting a function rather than splitting it up into sub functions
	* Comments that reference non local inforomation

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

CONTINUE

-----------------------------------------------------

### 7. Exception and Error Handling

Try to avoid return codes, instead use exceptions. Your exceptions should be clear and show what type of error has occured.

When using a try-catch block, think if this happens -> this should be done

---------------------------------------------------------

### 8. Boundaries

Dont pass objects that are often changed around your code. 

-----------------

### 9. Unit Tests

Your automated tests should cover all of your codes functionality.

You should do this in a TDD approach (Write the test -> Write the minimal amount of code to pass the test)

Test should be fast and independant of each other

------------------

### 10. Classes

Place your constants first, then variables, then methods.

This applies in methods as well (Constants, variables then method body)

Keep utility methods and all variables private.

Classes should be a small as possible, and should have on responibility ( Remember S.O.L.I.D)

Class Cohension = A method that accesses more of the class's variables is more cohesive to the class.  Aim for high cohesion.

----

### 11. Systems.

TO DO

---

### 12. Emergency.

Remember Kent Becks 4 rules for simple design:

1. Runs all test
2. Contains no duplication
3. Expresses the programmers intent
4. Has only the needed classes and methods (Keep things to a minimal)

-----

### 13. Concurrency

Keep mangagement for concurrency seperate from your other code

Limit the access data that your threads will use. Use copies of the data.

Know what will be thread safe/ is not thread safe, blocking/non blocking.

Understand the key concepts of concurrency, deadlocks, mutual exclusion ect...

----

### 14. Successive Refinements

TO DO

----

### 15. JUnit Internals

TO DO

----
### 16. Refactoring 

TO DO
---

### 17. Smells and Heuristics

TO DO