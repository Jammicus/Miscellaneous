# The Art of Unit Testing - Robert C. Martin, Michael Feathers

---

## The Basics of Unit Testing

### Defining unit testing step by step

* A unit test is an automated piece of code that invokes the unit of work being tested, and then checks some assumptions about a single end result of that unit. A unit test is almost always written usinig a unit testing framework. It can be wirrten easily and runs quickly. It's trustworthy, readable and maintainable. It's consistent in its results as long as production code hasn't changed.
* SUT stands for system under test. When testing, you refer to the thing you're testing as the SUT
* A unit of work is the sum of actions that take place between the invocation of a public method in the system and a single noticable end result by a test of that system.
	* The end result can be any of the following:
		* The invoked public method returns a value
		* Theres a noticable change to the state or behavior of the system before and after invocation that can be determined without interrogating private state
		* Theres a callout to a third-party system over which the test has no control, and that third-party system doesnt return any value, or any return value from that system is ignored.

### Properties of a good unit test

* Unit tests should meet the following properties:
	* It should be automated and repeatable
	* It should be easy to implement
	* It should be relevant tomorrow
	* Anyone should be able to run it at the push of a button
	* It should run quickly
	* It should be consisent in its results (Always returns the same result if you do not change anything between runs)
	* It should have full control of the unit under test
	* It should befully isolated (Runs independently of other tests)
	* When it fails, it should be easy to detect what was expected  and determine how to pinpoint the problem
* If you answer no to any of the following, it is not a unit test.
	* Can I run and get results from a unit test i wrote two weeks or months or years ago?
	* Can any memeber of my team run and get results from unit tests I wrote two months ago?
	* Can i run all the unit tests i've written in no more than a few minutes?
	* Can I run all the unit tests I've written at the push of a button?
	* Can I write a basic test in no more than a few minutes?

### Integration Tests

* These are any tests that are not fast and consistent, and use one or more real dependencies of the units under control. 
	* Examples of these could be tests that use the current system time. This will always be unique!
* Integration tests increase the resk of testing too many things at once
* Integration testing is testing a unit of work without having full control over all of it and using one or more of its real dependancies, such as time, network, database, threats, random number generators and so on.
* A regression is one or more units of work that once worked and now don't

### Test-driven Development

TDD Steps:

1. Write a failing test to prove code or functionality is missing from the end product. (You write this as if the production code were already working)
2. Make the test pass by writing production code that meets the expectations of your test.
3. Refactor your code. 

* Refactoring = Changing a piece of code without changing its functionality.

### The Three Core Skills of Successfufl TDD

* Knowing how to write good tests
* Writing them test-first
* Designing them well

## A First Unit Test

* You should have one test class per tested class. 
* For a unit of work, your test method should have the following format: `[UnitOfWorkName]_[ScenarioUnderTest]_[ExpectedBehavior]`
	* UnutOfWorkName = The name of the method of group of methods or classes you are testing
	* Scenario = The conditions under which the test is tested, such as  "bad login'
	* Expected behavior = What you expect the tested method to do under the specified conditions. These can be:
		* Returning a value as a result
		* Changing the state of the system as a result 
		* Call a third party system as a result

Eg, `IsValidLogInFailed()` could be refactored to be called: `IsValidFileName_BadExtension_ReturnsFalse()`

### Writing Your First Test

* Unit tests compromise of three main actions:
	* Arrange objects, creating and setting them up as neccessary
	* Act on an object
	* Assert that something is as expected
* Unit testing frameworks have assert methodas you should use!

Example

```
 public void IsValidFileName_BadExtension_ReturnsFalse() {     LogAnalyzer analyzer = new LogAnalyzer();     bool result = analyzer.IsValidLogFileName("filewithbadextension.foo");     Assert.False(result); }

```

### Setup and teardown

* Setups are used to ensure that the program is in the correct state before the test
* Tear downs are used to ensure the program is put back into the correct state after the test has occured
* Generally,these are ran before and after each test. However, some frameworks allow you to specify which tests setups and tear downs should be ran before/after
* You should avoid using these, They make tests less understandable


## Using Stubs to Break Dependencies

### Introducting Stubs

* Stub is a controllable replacement for an existing dependency in the system.
* Testing using a stub allows you to test your code without dealing with the dependency directly
* External dependencys are objects in your system that your code under test interacts with and over which you have no control (Eg, filesystems, threads so on)
* A tub is a controllable replacement for an existing dependancy in the system. By using a stub, you can test your code without dealing with the dependency directly


**CONTINUE THIS CHAPTER**


## Interaction Testing Using Mock Objects

* You should use mock objects when you want to test how your object interacts with other objects
* Aim to have no more than one mock and stub per test

### Value-Based vs. State-Based vs Interaction Testing

* Interaction testing is testing how an object sends messages (calls methods) to other objects. You use interaction testing when calling another object is the end result of a specific unit of work.
* Can also think of it as Action Driven testing (Testing a particular action an object takes)
* **Action testing should only be chosen as the last resort**
* Mock objects are fake objects in the system that decides whether the unit test has passed or failed. It does this by checking that the object under test calls the fake object as expecting. Generally there is no more than one mock per test
* Fakes are a term used to describe either a stub or a mack object. If it checks an interaction, its a mock, otherwise, its a stub

### The Difference between Mocks and Stubs

* Stubs can never fail a test. The asserts that the test uses are always against the class under test
* Mock objects are used to verify whether or not the test has failed

### Fake Chains: Stubs that produce Mocks or Other Stubs

CONTINUE


### The Problems with handwritten Mocks are stubs

* Takes time to write the mocks and stubs
* Difficult to write stubs and mocks for  classes and interfaces which have many methods, properties and events
* Saving the state for multiple calls of a mock method will result in a lot of boilerplate code within the handwritten files
* If you need to verify that all parameters on a method call were send correctly by the caller, many asserts will be needed
* Hard to reuse mock and stub code for other tests
* Is there a case for a fake which is both a mock and a stub?

##  Isolation (Mocking) Frameworks

* Isolation frameworks are a reusable library that can create and configure fake objects at runtime
* Objects they create are referred to as dynamic stubs and dynamic mocks
* Definiton: An isolation framework is a set of programmable apis that make creating fake objects much sipler, faster, and shorter than hand-coding them