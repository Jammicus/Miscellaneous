# Refactoring - Code Smells


From: https://sourcemaking.com/refactoring/smells

------

## Bloaters


### Long Methods
Signs:

* Method is  > 10 lines
* The need to comment the method to make it understandable

Fix:

* Split the method up using ` Extract Method `
* Have a composed method (Method that only calls other methods)


### Large Class
Signs:

* Class has >100 lines of code

Fix:

* Split the class up (Think carefully about the methods, would it make more sense to put some in a different class?) using ` Extract Class ` or  `Extract Subclass ` or ` Extract Interface `



### Primitive Obsession
Signs:

* Many primitives used in a class for simple tasks (Eg, a name string, a currency string...)
* Constants being used for simple things
* Using contstants for names in arrays

Fix:

* Create a object instead using `Replace Data Value with Object`
* Move the behaviour and the data into a seperate class

### Long Parameter List

Signs: 

* > 4 parameters for a givenmethod

Fix: 

* Pass an object rather than multiple values.
* If data is unrelated, use `introduce parameter object `.
* If some of the arguments are results of methods calls on another object, use `replace parameter with method `

### Data Clumps

Signs:

* Different parts of the code have duplicate groups of variables

Fix:

* If the data is fields of a class, make a new class using ` Extract Class `
* If the data clump is passed as parameters to methods, use ` Introduce parameter object` 
* If data is passed to other methods, pass the entire object instead of parts of the object. Use ` Preserve whole Object `

------
## Change Preventers

### Divergent Change

Signs:

* Having to change many unrelated methods when refactoring a class

Fix:

* Split the class into seperate classes based on behaviors, use ` Extract Class `
* If different classes have the same behavior, use inheritance by ` Extract Superclass ` or ` Extract subclasss` 

### Shotgun Surgery

Signs:

* Any modification requires you to make changes to many classes

Fix:

* Move the existing classes behaviours into a single class by using ` Move Method ` and `Move Field `

### Parallel Inheritance Hierarchies

Signs:

* Creating a subclass for one class forces you to have to make a sub class for another class

Fix:

* Make all the instances of one hierarchy refer to instances of the other hierarchy, then remove the hierarhy that the referred classes uses by using ` Move Method` and `Move Field `

------------

## Couplers

### Feature Envy

Signs:

* Methods uses data of other objects more often than it uses its own data

Fix:

* Make sure that things that change together, are together
* Move the method if its in the wrong place using `Move Method`
* Move the method to the class that it uses most of the functions from using ` Extact method `

### Inappropriate Intimacy

Signs:

* A class is using fields and methods of another class


Fix:

* Move the methods and fields to where they are used.
* Extract the class using ` Extract Class `

### Message Chains

Signs:

* Your code calls a series of objects in one line.

Fix:

* Remove the chain using ` Hide Delegate `


### Middle Man

Signs:

* You have one class that has an action which makes another class do the work.

Fix:

* If a class mainly delegates work to another class, remove that class

### Incomplete Library Class

Signs:

* A given library is no longer meeting a users needs

Fix:

* Change the class library using ` Introduce Local Extension `

--------
## Dispensables

### Comments

Signs:

* Method is full of explanatory comments

Fix:

* Make sure your class names and methods are self explanitory
* If you need to assert rules for the state, use `Introduce Assertion `

### Duplicate Code

Signs:

* Two sections of code a virually identical

Fix:

* If the same code is in two or more methods in the same class, use ` Extract Method `
* If code is duplicated in multiple classes, use Extract Superclass `

### Lazy Class

Signs:

* Class is rarely used, or if used, does not do much

Fix:

* Rehome the methods and remove that class.

### Data Class

Signs:

* A class that refers to another class that only contains fields and the relevent getters and setters

Fix:

* `Encapsulate Field` for the public methods
* ` Encapsulate collection` for data stored in arrays, lists ect...

### Dead Code

Signs:

* Methods / Variables that are not used annymore

Fix:

* Remove them

### Speculative Generality

Signs:

* "Just in case " code
* Does not seem logical to have this code

Fix:

* Remove it
* If methods, use ` Inline Method `
* If a parameter, use ` Remove Parameter `

-------
## Object-Orientation Abusers

### Switch Statements

Signs:

* Complex switch statement
* Complex If statements

Fix:

* Move the switch statement to the correct class using ` Extract Method -> Move Method `
* Try to use polymorphism by using ` Replace Conditional With Polymorphism ` 
* If many conditionals that all call the same method with different parameters, use ` Replace Parameter With Explicit Methods`
* If using NULL, use ` Introduce Null Object `

###Temporary Field

Signs:

* Fields that are only used under certain circumstances. 
* Often these fields have no value the majority of the time.

Fix:

* Move the field and the code working on that field into another class using ` Extract Class ` and `Replace Method with Method Object`

### Refused Bequest

Signs:

* Subclass only uses some methods/fields from its parent class

Fix:

* If the subclass has nothing in common with the parent class, remove the inheritance with ` Replace Inheritance with Delegation`
* If the inheritance makes sense, remove the unneeded fields and methods and put into another Superclass

### Alternative Classes with Different Interfaces

Signs:

* Two classes perform indentically but use different method names

Fix:

* Refactor the methods so it works on both classes 


------
