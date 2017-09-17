# Selenium Design Patterns and Best Practices



## The Record and Playback Pattern

* This is the starting point of many automated user interface testing tools.
* Idea is to allow the user to record their normal testing activities and play them back through the testing tool at a later date

### Advantages of the Record and Playback Pattern

* Fast test growth - Users can record new individual tests as fast as he or she can click on links
* No previous programming experience needed - Just hit record and execute the test
* Element lookup - Easy to look up elements in the page source by hand

### Disadvantages of the Record and Playback Pattern

* Bad locators - Tool will often need the absolute path to an element
* Inflexible tests - Tests will be identical to the original recording
* Hardcoded test data
* Poorly written tests (What you see is what you get)

## The Spaghetti Pattern

* This is an anti-pattern
* This is characterized by lack of perceived architecture and design
* Concept is a bowl of spaghetti, where each strand of spaghetti can represent a single or multiple tests which are so tightly intertwined that it becomes difficult to tell them apart.
* Tests in this pattern are strongly dependent on the execution order of all the tests, and over share internal private components with each other.

### Advantages of the Spaghetti Pattern

* Quick start - No need to sit down and plan ahead.
* Smaller code base - As all tests depend on each other, no need to repeat test actions within individual tests
* Smoke tests - These are fast, brief and leave as small a test data footprint as possible.

### Disadvantages of the Spaghetti Pattern

* Anti-pattern - This will lead to long-term maintainability problems (Hence why it is an anti pattern)
* Tight coupling - Prevents code reusability and lads to duplication
* No parallel test runs - Will be unable to run different tests at the same time
* Covers up failures - A failure in the beginning of the test suite will prevent the execution of the entire suite
* No resilience

## Introducing Locator Strategies

* ID - Finds an element by its ID. By far the best way to locate any element as you do not have to deal with surrounding or parent elements
* Class name - Locates element(s) with a given class name
* Link test - Finds a link that has an exact test in it
* Partial link text - Same as link text but allows a wild card search for partial text match
* Name - Searches for all elements that have a name property
* Tag name - This searches for an element's tag name, such as input or label
* CSS selector - Searches for elements with custom - written CSS selector style query
* XPath - Searches for elements with custom-written xpath style query

## Using Advanced Locator Strategies

* Absolute Path - Very detailed instructions on how to get to the element, however is very rigid
* Relative Path - more flexibly than absolute path, but as it is not defined as strictly, it may get the wrong element or multiple elements

## The Chain Linked Pattern

* Improvement on the Spaghetti pattern
* Unlike the bowl of spaghetti, an outstretched length of chain can characterize this pattern
* each link in the chain is a individual test and its own entity.
* This however still relies on rigid execution
* Improvement over the Spaghetti pattern as it segregates individual tests into more or less self-contained units

## The Big Ball of Mud Pattern

* Does not have any format structures that will allow a distinction between any individual components
* Test data and results are promiscuously shared amongst most distant and unrelated components until everything is global and mutable without warning
* Unintentional test failures will occur when a component is changed for a new test without the realization that hundreds of other tests depend on it.
* Compared to the spaghetti pattern, this state of affairs is in much more dire need of repair
* Avoid this at all costs

## Refactoring Tests

### The DRY testing Pattern

* **Treating automated tests with the same care and respect as the application that we are trying to test is the key to long-term success**
* DRY = Don't repeat yourself
* Remove all unnecessary duplication
* This also includes removing duplicate test goals
* Aim is to try to avoid accidentally testing any functionality not related to the current test

### Advantages of DRY

* Modular tests - Tests and test implementations are self-sufficient. Tests can run in any order.
* Test actions such as clicking or registering a new user are shared during tests
* Reduced duplication - All actions such as filling out a form are kept into one place
* Fast updates - Unique actions in a single place make it easy to update the tests
* No junk code

### Disadvantages of the DRY testing pattern

* Complicated project structures
* Lac of a good IDE - Many IDEs will not notify the developer if a test action has already been implemented
* Constant upkeep - Keeping the suite clean and applying the DRY test pattern will need dedication from the team
* Programming Skills - This needs to be improved by the whole team. Bad developers will ruin the code

## Moving Code into a setup and teardown

* Setups is ran before tests to get the environment into a test-ready state
* The teardown is used to clean up after the tests to put the environment back into a pristine state
* Some frameworks allow setups and tear-downs before and after each individual test, others only after a group of tests

## Hermetic Test pattern

* Polar opposite of the Spaghetti pattern
* Each test should be independent and self-sufficient.
* Any dependency on other tests or third-party services that cannot be controlled should be avoided at all costs
* Its impossible to get a perfectly hermetically seated test, but when a dependency on anything outside the test is detected, it should be removed as soon as possible

### Advantages of the Hermetic test pattern

* Clean start - Each test has a cleaned up environment to work in. This prevents accidental test pollution from previous tests
* Resilience - Each test is responsible for its own environment
* Modular - Each test is standalone and can be arranged into smaller test suites such as smoke suite or can run as a standalone test
* Random run order practice - As they are not dependent on other tests, can be ran in any order
* Allows parallel testing - This can significantly reduce the runtime of the test suite

### Disadvantages of the Hermetic test pattern

* Upfront design - Tests must be designed to be self-sufficient. Tests can reuse other methods, but cannot reuse data and test results from other tests
* Runtime increase - As tests must setup the environment before it starts, this increases test execution time
* Resource usage increase

## Using Timestamps as test data

* Great way to guarantee unique data

## The Random Run order Principle

* The order of the test suite execution should be randomized every time the suite is executed.
* This should flush out instabilities in the test suite by introducing an element of chaos

### Advantages of the Random Run Order Principle

* Prevents test interdependence - Tests that depends on another test to set up the environment will be exposed rather quickly
* Flushes out data pollution - Can easily tell if a test leaves the environment in a bad state after completion
* Built in - Some frameworks support test randomization out of the box and also have the random run order as a default setting

### Disadvantages of the random run order principle

* A lot of refactoring - If the suite is a mess, will require a lot of work to get this principle working
* Random run audits -  Can be hard to find the sequence of tests that cause instabilities due to random run order
* Team frustrating - Running tests in a random order can create a lot of frustration and resentment for the whole time.
* No built in support - Many test frameworks do not support test randomization. Implementing this functionality might be very difficult

## Data Driven Testing

### Hardcoding input data

* Tests should within reason be able to run on any environment we have
* This is not possible if we hardcode the input data

### Hiding test data from tests

* To make our tests flexible enough to work on any test environment we want, we need to provide them with data applicable to the said environment.
* The test itself does not need to know what data we are using
When data is hidden correctly, the test will not care what username and password is used, the information is fed into the test from the outside and is stored in variable
* This can be done by using environment variables

### Choosing the test environment

* Use environment variables
* Using them can easily alter the applications behavior.
* Eg `set environment = staging`
* In your test code create methods that will get the environment variable set on the current system.

### Introducing test fixtures

* A test fixtures are a term used to describe any test data that lives outside of that particular test, and is used to set the application to a known fixed state
* Fixtures allow us to have a constant to compare individual test runs against.
* See the book for more information (This is particularly suited to E commerce websites)

CONTINUE HERE ##############

## Stabilizing The Tests

* When test suites become large enough, our job becomes less about fixing eery flay test. It now centers on engineering a solution that will prevent all similar flaky behavior from happening.

### Engineering the culture of stability

* The key goals for any CI system should be:
	* Running fast and failing fast
	* Running as often as possible
	* Keeping a clean and consistent environment
	* Discarding bad code changes
	* Maintaining a stable test suite

### Running fast and failing fast
* Developer time is expensive
* Sitting for 40 minutes to see whether a test fails is a terrible waste of time

### Running as often as possible
* Creating a cascading build chain, starting with unit tests and finished with Selenium, is common practice
* This has turned out be a anti pattern, specifically the spaghetti pattern.
* Selenium builds are the slowest in the series, and occupies the last place where everyone can easily ignore it.
* Making sure that the selenium build is triggered on every single commit seems excessive, but the whole idea of CI is to catch a test failure as soon as it occurs.

### Keeping a clean and consistent environment

* Reloading the test database for every build is a great way to keep a clean and consistent test environment
* Using configuration management tool to keep all of the dependencies, such as java versions, consistent for all the test nodes will save you headaches

### Discarding bad code changes

* Set up a simple system that prevents anybody from committing changes to the master/trunk unless all tests, including selenium, were passing.
* If you have a stable test suite, this helps prevent unintended defects from going into production and making sure that the whole test suite, including selenium, was always passing

### Implementing Intelligent Delays

* When you know that animations need to occur or certain events need to occur, use delays
* A fluent wait/delay polls until the element is in or out of the DOM
* A explicit wait, waits until the end of a set time

### The Action Wrapper Pattern

* Idea is to collect all the most common pain points, and automatically implement measures to prevent issues for these pain points as soon as that action is performed
* This helps to future proof the tests by automatically accounting for things that commonly go wrong and destabilize the tests

#### Advantages of the Action Wrapper Pattern

* Single location for auctions - Actions like clicking, typing ect are in a  single class. Encourages DRY
* Increased overall build stability - The test suite becomes a lot more stable since forgetting to add a wait no longer breaks random tests at random times
*  Capture and append exceptions - IF an action cannot be performed, we can capture the stack trade and add more information for better debugging
*  Helps to implement screenshot pattern : Makes it easier to add functionality that will capture screenshots of the whole web page on test failures

#### Disadvantages of the Action Wrapper pattern

* Adds increased time to the tests

### The Black Hole Proxy Pattern

* Tries to reduce test instability by getting rid of as many third-party uncertainties as possible.

#### Advantages of the black hole proxy pattern

* Improved speedy - Web pages will load faster as we do not have to wait for third-party content to load
* Improved Stability
* Hermetically sealed tests - test has higher control over the environment. By blocking third-party content, we reduce external dependencies that cause test failure

#### Disadvantages of the Black Hole Proxy Pattern

* Broken Layout - will be missing all third party content
* Third-party content tests are broken


See book for implementation details


## Testing The Behavior

### Behavior-driven Development

* Given-When-Then

#### Advantages of BDD

* Better test understanding
* Modular implementation - methods thats that perform the actual implementation can be shared while testing
* Versatile implementation options - By sticking close to behavior, it is easy to have one defined behavior running in multiple environments
* Multiple BDD frameworks
* Data separation

#### Disadvantages of BDD

* Easy to mix behavior and implementation - Can be  be tempting to start adding implementation into the definition
* Wide range of tools to choose from
* Added overhead
* Learning curve for each new frame work


### The Write once, test everywhere pattern

* Concept centers on taking advantage of shared behavior between multiple implementations of one application

#### Advantages of the write once, test everywhere pattern
 * Foresight - This pattern forces the architect of the test suite to think ahead and boil down every feature and behaviour to the simplest, most common list of ideas
 * Reusability - Can be reused between the mobile and website test suite ect
 * Simplicity - We have a single test suite that runs on multiple platforms and shares some of the implementation details

#### Disadvantages of the write once, test everywhere pattern

* Runtime content switching
* Complex code base - Combining multiple test suites into one has a lot of advantages, however, the project structure might become convoluted and difficult to understand very

## The Page Objects Pattern

*  Idea is to make each page into a object, with fields that represent areas of that page

```
Page homePage = new Page()
homePage.header =PageHeader;
homePage.footer =pagefooter;

```

### The Page Objects Pattern

* Describes any webpage in terms of a hierarchical Domain Specific Language (DSL)
* Application specific DSL helps to hide the page implementation, so the test is no longer allowed to directly interact with the page, but instead uses a framework to classes and methods to accomplish the same goal.

#### Advantages of the Page Object Pattern

* Creates a DSL framework
* Testing Behaviours - very similar to BDD
* DRY
* Modular and reusable : As each Page Object is made from multiple smaller objects, the smaller objects (Eg, header and footer objects), these can be shared between multiple pages that have the same implementations of these objects
* Clear intentions - Intended actions can be clearly represented in code

#### Disadvantages of the page object pattern

* Complexity is increased when using Page Object Framework
* Programming design patterns should be followed to make the code consistent and easy to understand

### Creating a Page Object Framework

#### Create a page super class

* All pages should inherit this.
* This class should provide access to different parts of every page
* Eg when test needs to check the content of the shopping card in the sidebar, it will ask the current page for the Sidebar object, which will ask for the shoppingCart object from that object.

#### Creating page subclasses

* Inherit shared aspects of the page from the super class
* Add custom implementations for different aspects
* Each page should have methods to interact with aspects of that page which are different from the page super class
* Having some verification in these methods should be there (Eg, that something is added to the cart once the method is called)


## Growing the test suite

### Strategies for writing test suites

* Instead of having 100% test coverage, the best that can be done is to prioritize the growth of the test suites.
* Its best to have a way to group certain tests together so they can be executed individually.

### Different Types of Tests

* Unit tests - Smallest unit of tests . Written to test an individual object and even individual methods of said object. Selenium tests are not applicable here
* Integration tests - Consists of several modules of code put together, allowing them to pass data between each other. In terms of selenium, this could be logging in and adding an item to the card
* End-to-end - Highest level of test. Executed in production. Similar to integration tests, tries to verify that all the components including third-party services can communicate well with each other

### The Smoke Test Suite

* Idea is to plug in the new code, let it run, and see whether it runs or catches on fire.
* By far the smallest in size, as it needs to give a close to instantaneous pass for fail verdict
* Tests in the smoke test suite should look like the following:
	* Running the application: Does it give a 500 error? ect.
	* Database connectivity
	* Abnormal amount of exceptions - eg checking javascript logs for exceptions
* Smoke test suite should almost be like a feather in a boxing fight. Should leave the application without a single dent or scratch occurring:
	* Avoid writing to a database if you cannot clean it up after
	* Don't test too much

### The Money path suite

* Money paths are one or several core key pathways through our application (also known as happy paths)
* Money paths should answer the following questions:
	* Is the user blocked from doing a key activity. (Eg, adding items to the cart)

### New Feature Growth Strategy

* When writing tests for new features, the tests should answer the following questions:
	* IS this the most important and critical feature to be tested?  When pressed for time tests should aim to test mission critical features and leave the enhancements to the regression suite
	* As soon as a test is written, even if the feature is unfinished, it should be added to CI

### Bug-driven growth strategy

* Having an automated test case for every bug fixed in the current build is a great safety net.

### The Regression Suite

* Regression tests are all of the tests in our suite that test features developed in the past.

### Continuous Integration

* There are five components to setting up a CI system. In order of importance:
	* Test environment : Must have an application to test.
	* Test data
	* Tests and test stability
	* Test nodes: These need to be stable
	* CI System choice

### Managing the test environments and nodes

#### Build node management

* Ideally each node should be identical with the same versions of software and OS on them
* To approach this problem use:
	* Configuration management system
	* Virtualization

##### Configuration Management System.
* Ensures nodes are configured in the same way
* Key tools to ensure your nodes are identical:
	* Chef
	* Puppet
	* Shell scripts

##### Virtualization
* Uses virtual machines
* Some options for this:
	* Xen Project
	* Virtual box
	* Windows virtual PC


## FAQ

### What programming language to write tests in?

* Close to the integration - if application is being tested is written on a JVM platform, uses a language that is jVM compatible
* Developer involvement - use a language developers are comfortable with

### Can I use selenium for performance testing?

* Selenium is a terrible solution for performance testing.
* YSlow is good for checking what assets are slow to load
* You can write scripts in ruby or bash that make hTTP requests against different API endpoints or assets and records the time it took to complete a purchase request or for an image to download
