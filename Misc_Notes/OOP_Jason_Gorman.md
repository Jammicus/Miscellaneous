# Object Orientated Design Principles - Jason Gorman

---

## Refactoring Foundations

* Doing changes during the requirements phase is considerably easier than doing it later in the project lifecycle
* Refactoring = Changing the design of the eisting code without breaking it
* Refactoring process:
	1. Run Tests
	2. Refactor a single thing
	3. Loop back to 1. 
* Best way to future proof your code is to make it simple, rather than trying to predict the future

--

## What Makes Code Harder To Change?

* Bad readability
* High amount of dependability (The ripple effect)
* Lack of code
* High code complexity
* Duplication

--

## Code Smells

* Code smells are problems with the code
* Types of code smells:
	* Increasing Complexity
	* Increasing duplexity
	* Increasing depedancys 
	* Decreasing Comprehensity

--

## Classes of Code Smells

* Complexity:
	* Large methods
	* Data clumps
	* Long parameters lists	
* Responsibiity:
	* Divergent change
	* Data clases
* Couples
	* Feature envy (Where classes are using a feature it should not)
	* MEssage chains
* OO Abuses
	* Switch statements (You should be using polymorphism)
* Redundancy 
	* Duplications in the code

--

## Refactoring Long Methods

* Split into smaller methods
* Have the old method call the new method(s) (A method that only calls other methods is called a **Composed Method**
* Remember that a method should only do one thing

---

## Good Refactoring Habits

* Run tests after every refactor
* If a refactoring fails tests, undo/roll back
* Identify code smells and use the appropriate refactoring
* Check-in ater every refactoring goal is met
* Never refactor while there is a failing test
* Use automated refactorings that your IDE provides you whenever possbile
* Do one refactoring at a time

--

## Goals of OO Design

* Putting data, functions and interfaces together
* Allowing us to "swap" parts by polymorphism
* Ability to make changes to one part of the sytem, rather than being force to do this for muiple 
* Managing the dependancies of your code

--
## Types of Dependancies

* Efferent Couplings - These classes depending on something
* Afferent coupling -These classes have other classes depending on them

``` EfferentClass -> AfferentClass ```

--
## Coupling & Cohesion

* Internal Dependances - Methods and fields in the same class depend on each other
* Class coupling - Given class relies on another class (Has an Efferenct coupling)
* Cohesion - The degree that things that change together are in the same place
	* High cohesion of a class = Changes happen only in that class (Ideal)
	* Low cohesion of a class = Changes done in one class effect other classes
* Class Choension formula = Number of internal dependancies on other classes / all methods of the class (including the constructor

---

## 4 Rules of Dependancy Management

1. Minimise dependancies - Have less code
2. Localise dependancies - Package dependant methods, fields and classes together
3. Stabilise Dependancies - Depend on things that are unlikely to change
4. Abstract Dependancies - Depend on things that have the ability to be substitued

----

## Basic Design Principles

* Less code = less dependancies
	* Take your time
	* Is there a simplier way to do this?
	* If unsure, sleep  on it
* Don't repeat yourself
	* Duplicated code = duplicated dependancies
* Tell, dont ask
	* Tell the objects that  hold the data to do  the work on that data
	* If a method does not  have the data it needs, its probably the wrong method or in the wrong place

--

## Class Design Principles (S.O.L.I.D)

* Single Responsibility
	* Classes should only have one reason to change
	* Classes should only do one thing
	* This gives us the ability to reuse this class else where
* Open Close
	* Open to extension (For Classes & Dependancies)
	* Closed to modification
	* Open to substitution
	* Remeber when doing this not to break the classes contract!
* Liskov Substitution
	* An instance of a class should have the ability to be substitued with an instance of any of its subclasses
	* When you extend classes you can either make the preconditions(Something that must always be true when giving something to this class) of a class stronger, or the postconditions(Something that must be true when sending data from the class) strong
	* You should test the new classes against the original tests/contract
* Interface segrigation
	* Classes should present client-specific interfaces
	* You should split classes into two interfaces with only the methods a class should need
	* Don't think of the objects type, think about what they need to see
* Dependancy Inversion
	* Abstract your dependancies
	* Dependancies should be easy to swap without breaking anything
	* High level modules should not depend on a low level module
	* Abstractions should have higher affluent couplings
	* Concrete clases should have higher efferent couplings 

**TO DO: Formulas for Dependancy inversion**	
--

## Package Design Principles

* Package = Unit of code release (Has been released and gone through the relevent release process)
* If we are reusing of code, the package must have been through the release process

--

## Release Reuse

* The unit of reuse is the unit of release
* 1st order reuse = Has been through the release process

--

## Acyclic Dependancies

* This is where there is a loop on package dependancies
	* Eg, A -> B ->C -> A
* This causes you to build everything
* You should understand whether or not a component should or why it depends on something and how they conntect to other components

--

## Common Closure

* Classes that change together, belong in the same package
* Package things that are commonly used together

--
## Package Cohesion Metrics

* Package Cohesion = `Average Number of Internal Relationships Per Class / Number of classes`

--

## More Class Design Principles

* Law Of Demeter
	* Classses should only know their nearest neighbour (methods should not call a neighbour of your neighbours class
	* Think of how classes collaberate, not data objects
* Reused Abstractions
	* Classes are clostly, abstractions should be used at least once
	* Interfaces and abstract classes should be implemented/extend by more that one class & only made when necessary
* Stable Dependancies
	* Packages should only depend on dependancies that do not often change
* Stable Abstractions
	* The abstractness of a package should be in proportion to its stability
	* The more stable a class is, the more abstract it should be
	* `Abstractions (A) = AbstractClasses/AllClasses`
	* High level modules and low level modules should depend on something abstract to join them

--

## OO Design Level

* Write the simpliest code as possible
* Refactor mercilesssly to remove duplication
* Put the behaviour where the data is
* Ensure classes and methods only do one thing
* Restrict interactions to a small number of direct collaberators
* Favour fewer high level interactions
* Test that subclasses satisfy super-classes contract
* Package dependant clases together as much as pobbile
* Continously analyse & manage dependancies
* Ensure your design makes sense in the application domain
	