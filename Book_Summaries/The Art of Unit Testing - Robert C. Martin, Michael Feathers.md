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

*