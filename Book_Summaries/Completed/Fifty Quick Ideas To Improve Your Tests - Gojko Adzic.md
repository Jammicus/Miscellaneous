# Fifty Quick Ideas To Improve Your Tests - Gojko Adzic


-------------------------


# Generating Test Ideas

* Software quality pyramid:
	* Does it work? What are the key features, key technical qualities
	* Does it work well? What are the key performance, security, scalability aspects
	* Is it usable? What are they key usability scenarios?
	* Is it useful? What production metrics will show that it is used in real work?
	* Is it successful? What business metrics will show that this was worth doing? Is it operating within financial constraints?

## Explore capabilities, not features

* Story-oriented exploratory testing sessions lead to tunnel vision and prevent teams from getting the most out of their effort
* Exploratory testing is most powerful when it deals with the unexpected and the unknown.
* Testing cant be focused purely on features
* Good ways to look for unexpected risks is not to explore features, but related capabilities.
* Focusing on exploratory testing on capabilities instead of features leads to deeper insights and prevents tunnel vision
* Make this work by focusing on the what the user has to do in order to do something, rather than what they want to do.

## Start With Always/Never

* To paint the big picture quickly, start off with a ten-minute session on identifying things that should always happen, or should never happen
* This should not be done by a single person. Several groups should brainstorm and then a list should be created from both

## Tap Into Your Emotions

* Having a heuristic for test design can stimulate some very useful discussions and upturn some stones that otherwise might have been left untouched.
* The heuristics proposed are based on nine emotions or types of behaviour (Remember this as ShadedFigs):
	* Scary
		* Areas of the highest risk to the stake holders
	* Happy
		* Simplest path through the particular area of behaviour and functionality you can thing of. This is expected to pass every time
	* Angry
		* Tests which we think will make the application react badly, throw errors, and get cross with us for not playing nicely (Validation errors, bad inputs, logic errors)
	* Delinquent
		* Security risks, like authentication, authorisation, permissions, data confidentiality so on
	* Embarrassing
		* Things that if they broke would cause huge embarrassment all round (Eg, bad spellings)
	* Desolate
		* Providing the application with zeros, nulls, blanks, missing bada so on
	* Forgetful
		* Fill up all the memory and CPU capacity so that the application has nowhere left to store anything. What does it lose?
	* Indecisive
		* Simulate being an indecisive user, go back, go forward, amend stuff
	* Greedy
		* Select everything, tick every box, opt into every option, order lots of everything. Trying to do the max of any action
	* Stressful
		* Find the breaking point of the functions and components so you can see what scale of solution you currently have and give you projects for future changes in business values
* To make this work : Start off doing the happy path, and look along it for alternatives

## Test Benefit as Well as Implementation

* You should describe your test through implementation details, rather than potential benefits
* You're looking for whether the implementation of the benefit is done well, rather than whether than the presence of that feature
* Instead of asking "does it work?", ask **"How would you know if it actually works well"**

## Quantify even if you cannot measure

* Qualities that are hardly measured rarely get the testing attention they deserve (Eg, usability or performance)
* They are often inspected as an afterthought, typically when someone complains
* Just because something is difficult to test, we shouldn't give up on capturing or expressing expectations.
* Even if you're not going to actively measure an important aspect of quality, try to quantify it
* Try to capture key representative scenarios that are good indicators of speed by working with the stake holders (Eg, instead of the homepage having to be "fast", select scenarios such as logging in, adding things to the basket, and try to quantify how fast each of these scenarios should be)

## Organise Test Ideas using an ACC Matrix

* Its hard to establish clear, impartial and objective criterion for how much testing is enough.
* Attribute-component-capability matrixes can be helpful here.
* It charts different capabilities in relation to system components and quality attributes.
* its a table in which columns have the names of quality attributes and system components are represented by rows
* Capabilities should be high levelled, and they should describe a whole range of scenarios.
* The guidelines for identifying capabilities:
	* Write a capability as an action, ideally from the sense of a user accomplishing some task
	* Provide enough information for a tester to understand what variables are involved in the related test cases, and do not aim to provide full details of the test cases
	* A capability should work together with other capabilities. Don't aim to describe a use case or a user story with a single capability.

## Use Risk Checklists For Cross-cutting Concerns

* These are where specific risks and concerns apply to a large set of things to test.
* This often leads to a lot of repetition and routine work, regardless of whether the tests are automated or manual
* Instead of describing individual test scenarios : Try to name the key risks in global checklists
* This helps QA to explore the right things, and prevents skipping critical risks.
* These should be quick and simple steps that are easy to check

## Document Trust Boundaries

* With different teams, trust boundaries are contracts between teams as to how things should be.
* You should explicitly identify and document trust boundaries as a group, including developers, testers and business take holders
* Identify how much you trust another team or vendor, and identify whether you need to test against them rigorously, or can you test less firmly

## Monitor Trends In logs and consoles

* System logs and consoles are often the only reliable source of information about what really goes on in complex workflows or systems with many components.
* Having a good understanding of how a log should appear will help you identify changes, which could be good or bad, quickly

## Mob Your Test Sessions

* Have test sessions with various people
* Each person will have their own goals and ideas, helping you to find pain points or concerns
* Start with the scope and purpose of the session, and go from there
* Give everyone a idea of the requirements, the acceptance criteria, the design, the test environment, the information objectives, and so on

## Don't let the pen be the bottleneck

* If there is a single pen being wielded by one person, it can lead to bottle necks waiting for the person to do their part
* Everyone should be able to contribute, and have full visibility of the process
* A good idea is to give everyone access to google documents, and allow them to comment on different aspects

## Snoop On The Competition

* When planning your testing activities, look at the competition for inspiration - The cheapest mistakes to fix are the ones already made by other people.
* When investigating support forums, look for patterns and categories rather than individual problems.
* Try to look at the root cause of analyses in the reports, and try to identify similar categories of problems in your software that could be caused by the same root causes

# Designing Good Checks

## Focus on Key Examples

* User stories need clear, precise and testable acceptance criteria so that they can be objectively measured.
* Breaking down complex examples into several smaller and focused groups leads to more modular software.
* If your examples are too complex, your work on refining a story isn't complete
* To deal with complexity, look at the following:
	* Look for missing concepts
	* Group by commonality and focus only on variations
	* Split validation and processing
	* Summarise and explore important boundaries

## Contrast Examples With Counter-Examples

* Counter examples are cases that show when the feature does not apply, or when the new behaviour is not invoked.
* Example could be when there is not enough items in your shopping basket for an offer to apply
* To make it work, do the following in order:
	* Start with the simplest example you can think of that shows a scenario where the feature of business rule takes effect. Write scenarios for that
	* Underline the parts of the example that are most relevant to the feature or rule. Make sure you distinguish between inputs (eg, item type, currency) and outputs (free delivery)
	* For each output, identify a different possible value this output could take.
	* Repeat until you have a valid and an invalid example

## Describe What, Not How

* Common mistakes when describing acceptance criteria for a story is to mix the mechanics of test execution with the purpose of the test
* They describe what they want to test and how something will be tested all at once
* Avoid describing the mechanics of test execution or implementation details within user stories.
* Don't describe how you will the testing something. Keep it to what you want to test instead

Example

```
Scenario: pre-paid account purchases

Given a user with 10 USD in a pre-paid account
When the user attempts to buy a 7 USD ticket
Then the purchase is approved
And the user is left with 3 USD in the account
```

## Avoid Mathematic formulas

-

## Flip Equivalence Classes Between Input and Outputs

* Choosing a representative example for a whole class of items is one of the key techniques for good test design, and most people understand it intuitively
* Eg, Logging using external identity provides, you'd check with Facebook, Google and Twitter accounts
* Make sure all perspectives are considered, experiment with splitting into groups when you design equivalence classes.
* Get one group to focus on inputs, and another on outputs.


## Clearly Separate Inputs and Outputs

* For information captured in tables, its good to pull inputs to the left and keep outputs on the right.
* For information captured in sentences or bullet points, put inputs at the top and outputs at the bottom.

## Ask 'What happens instead'

* Waiting for an event instead of waiting for a period of time is the preferred way to testing asynchronous systems
* But when you need to check that something does not happen, there is not event to wait for. You have to wait for a set time
* Tests that wait for a set time are brittle, environment-dependent, and easily affected by many other factors.
* Good solution for this is to ask  "What happens instead?" and validate the resulting condition. (Eg, after period of time, check that the account has been logged out

## Use Given-When-Then in a strict Sequence

* You should keep that format, you should never have a given or another when after the then
* Have the given clauses in the past tense, the when in the present, and the future in then.
* This makes it clear that givens are preconditions and parameters, and then statements are post conditions and expectations.
* Make given and thens passive, they should describe values rather than actions.
* Make sure when is active, it should describe the action under test

## One Test, One Topic

Pretty self explanatory

## Treat Too Many Boundaries as A Modelling Problem

* Complex models are difficult to describe
* Software systems built to automate such models are very difficult to test.
* Difficult testing is a symptom, not a problem.
* Probe and evaluate potential models by experimenting with test case design before programming.
* If the model is difficult to describe with a relatively small number of key examples, try a different model

## Prefer Smaller Tables

* The power of tables is that they reduce a problem to the key relationships that matter, and remove as much semantic noise as possible.
* Depending on the number of rules, exceptions and nuances that affect the feature being specified, these tables of examples can grow quite large
* The best way to overcome this is to deal with one rule or concept at a time, and only include the subset of variables and example values that are relevant to it.
* Our feature specification would therefore consist of a set of connected concepts, each with small examples to illustrate it.
* Start by breaking big tables into groups of examples that are related to a single concept (Such as doing a SPOT trade). This will improve readability just by having several tables each with a fewer number of rows.
* Make sure each table has a brief text introduction to describe the concept or rule that the examples in the table illustrate.
* Link the related concepts and tables so that it is easy to navigate between related tables

## Balance Three Competing Forces

* BDD (Behaviour-driven development) test artefacts and executable specifications should ideally be designed to serve the following roles:
	* Specification (Of what needs to be implemented or changed)
	* Acceptance tests (for the specific cases to be checked as part of acceptance of this feature)
	* Documentation (Of the behaviour of this feature).
* To get the most value out of all three roles - you need to find a balance between the 'three c's' of executable specifications:
	* Conciseness (of specification)
	* Completeness (of test coverage)
	* Coherence (of documentation)
* Tips on how to do this:
	* Always provide introductory text for each set of examples
	* Show simple examples before more complex ones
	* Group small sets of related or complementary examples together
	* Highlight your key examples and keep them prominent in your specifications, close to the descriptions of the business rules they illustrate
	* If you also have more comprehensive set of tests that cover additional cases, keep these in separate tables or scenarios, or consider putting them in a separate feature file or page, and tag them accordingly


## Write Assertions First

* Starting from the outputs makes it highly unlikely that a test will try to check many different things at once, as those different aspects will naturally be split into different outputs.
* If tests grow too big or become too complex to understand, they are much easier to split into several tests when designed from an assertion first viewpoint rather than an input first viewpoint
* Try to use concrete values instead of general descriptions for outputs.
* The more concrete the outputs, the more difficult it is to hide wrong assumptions.

## Split Technical and Business Checks

* Many user stories involve both technical and business-oriented requirements. Eg automating credit card charge notifications might have an impact on transaction workflows and order management
* Mixing technical and business aspects in a single test gives the worst of both worlds.
* Dividing a single overarching test into several smaller and more focused tests make it much easier to understand and maintain all the test documents.


## Don't Automated Manual Tests


* Manual tests, even when its a detailed script, gives tester the opportunity to spot tangential information, such as unexpected events and layout problems.
* Manual tests provide most value when they are not executed by blindly following just what's written on a piece of paper, but by using the test more as a guideline for investigation.
* Manual tests work well when they provide the context, even if they leave out specifics.
* When teams decide to automate a set of existing tests that were previously designed as manual tests, the best way forward is to rewrite and redesign the tests from scratch.
* For manual tests, it saves time to check multiple things a single test. This is a very bad idea for automation - Automation should only ever check one thing
* Automated tests should check for deterministic, pre-defined outcomes, freeing up people to explore non-deterministic outputs and identify unexpected outcomes.

# Improving Testability

## Wrap Synchronous Database Tests in Transactions

* Tests involving a database require teams to make careful compromises between isolation, reliability and speed of feedback
* One option is for tests to talk to a production-like data source. This makes them very reliable, because the environment is which they run is similar to the tat of the target platform.
* Common alternative is for tests to execute using a simplified, minimised data set, which is faster to set up.
	* This speeds up feedback but sacrifices reliability.
	* Data-driven systems often experience problems when they hit unexpected real-word information, and tests running on an idealised, simple data set rarely encounter such problems.
* Another solution is to run tests against a specialised testing database.
	* Ideally object-oriented data access libraries should take care of database access, so the same test can in theory be executed against any type of data source.
	* This leads to tests with in-memory databases which require no disk access and can be started inside the test runner process. Feedback is much faster, tests are completely isolated, but unfortunately this approach makes tests high unreliable
* If the activity under tests is synchronous, and involves only one operating system process (Eg, its not distributed), wrap the tests in database transactions and rollback transactions at the end of each test

## Set Up Before Asynchronous data tests, don't clean up after

* Its better to clean up before a test executes, rather than after where there is an assumption that the test has passed.
* Many testing tools when a test has failed will not execute the cleaning up step.
* Its far more practical to clean up environments in test set-ups, before each test executes.
* Whenever possible, rely on set-up code to sort out an inconsistent data state.
* Feel free to include clean-up procedures after testing, but don't rely on them being always executed.
* Ideally, each test should be able to set up the external environment for itself, but sometimes this is not possible.
* In such cases, the set-up code should at least check if the external state is consistent enough for the test to execute, If it is not, issue an alert about the invalid starting position without allowing the test to run.
* Its much better to see an invalid state warning than a false failure

## Introduce Business Time

* Time-based features tend to be very difficult to test properly. Such as re-enabling buttons on a form after 300 millisecond animation
* Many teams will write a test that pauses for 300ms, then checks the button state.
* This is problematic as firstly its not really deterministic, and its delaying feedback
* A way of implementing business time is to separate out an application clock component, and make all other components use it instead of the operating system clock. Its then easy to roll this clock forwards and backwards. This approach however requires that the whole application stack is under the control of the delivery team.

## Provide Atomic External Resources

* Resources created asynchronously, or outside the main testing process, are one of the major causes of instability for automated tests.
* Failures from resources created outside the main testing process are extremely hard to debug.
* Whenever a test needs to access external resources, in particular if they are created asynchronously or transferred across networks, ensure that the resources are hidden until they are fully complete
* Make them atomic -  The appearance of the resource should also mean that it is ready for use.
* Atomic external resources prevent false alarms and save a lot of time by making test execution more reliable
* It makes resource handling easier in production systems. If tests can get incomplete data, it's highly likely that the underlying process in the system under test can experience the same problem.
* By designing atomic resource handling for tests, it becomes easier to provide such resources to production systems as well, and avoid occasional nasty bugs that are difficult to troubleshoot
* If possible design the system so that it creates a file of this type under a temporary name, and when it completes and closes the file, renames it in accordance with the final expected output.
* Writing file content is normally a buffered operation, so files may appear even though they are incomplete.
* Renaming on the other hand is an atomic operation. You can make the system use the file once it has been renamed to a specific state

## Wait For Events, not Time.

* Pretty self explanatory. Wait for an element or something to happen rather than waiting a set time expecting the event to happen

## Split Data Generators From Tests

* If you have to run a lot of tests driven by generated data, one of the best tricks to improve feedback and reduce maintenance costs is to completely decouple data generators from individual test scenarios.
* Write them as separate libraries, or even separate processes.
* If possible, save test data into files and use a simple data format.
* Avoid binary information if you can, and instead use human-readable text.
* Avoid position-based columns or complex nested structures and use separators such as commas that humans can understand.
* Decoupling generators from test execution does, however, introduce the problem of trust.
* If you're planning to use multiple generators for the same tests, or if you expect people to manually modify and craft input data, it might be a good idea to run some basic data validity checks on the data before a test.

## Minimise UI Interactions

* UI automation often makes tests unnecessarily slow, environment-dependent and fragile, severely limiting the effectiveness of tests.
* Sadly, the UI cannot be tested will just be deterministic checks. The many unexpected things can happen with a user interface mostly require a human eye to spot and a critical human brain to analyse.
* Minimising UI interactions makes tests faster and more reliable. The UI is often the slowest and the most brittle part of a system, and small changes in it break tests easily.
* Even when tests need to execute through the UI, minimise the part of the test that actually simulates user actions
* use suitable setup and clean down tasks for the test.

## Separate decisions, workflows and technical interactions

* Separate business specification and automation code (Like cucumber does)

## Use Production Metrics for Expensive Tests

* True tests for usability improvements is whether users are actually doing something faster or not.
* Instead of just accepting that something is difficult to test and ignoring it, investigate whether you can measure it in the production environment. If so, extend your testing strategy to include such measurements.
* Eg, time a user doing an action on the old system, then on the new system

# Managing Large Test Suites

## Make Developers Responsible for Checking

* By decoupling development and test automation, teams either introduce a lot of duplicated work, or unnecessarily delay feedback.
* The only economically sustainable way of writing and automating hundreds of tests is to make developers responsible for doing it.
* Avoid using specialist groups and test automation experts.
* Give people who implement functionality the responsibility to execute tests, and ensure they have the necessary information to do it properly.
* When the same people are responsible for implementing and changing code and automating the related tests, tests are generally automated a lot more reliably and execute much faster
* It is still important that you include the right people in designing the tests
* Its good practice to pair up developers and testers during automation work, and by running some quick exploratory tests to investigate the automation code

## Design Tests Together With Other Teams

* This way you can see how far their tests cover, and what you will need to cover

## Avoid Organising tests by work items

* When tests are organised according to business activities, not software work items, small business changes introduce small organisational changes for tests.
* This means that tests are easier to maintain.
* For consumer software, structuring tests around key user activities is often a good idea.
* For back-office enterprise software, structure tests around key work-flows or use cases.
* Its often useful to identify some initial testing ideas for work tasks as a starting point for team discussions.

## Version Control Tests Along With Software.

* Keep tests in git with your source code

## Create a gallery of examples for automation patterns

* When writing tests, you often have to choose between removing duplication and improving readability.
	* Generally its much more important to make tests easier to read than to ensure that each task is handled by only one piece of test code.
* If dealing with a complex system, there is probably a risk of different people automating the same thing in different ways just because its difficult to find the right information.
* Consider creating a gallery of automation examples for key aspects of your tests, and make the examples easily accessible.
* However, don't use a common gallery of examples as an excuse to enforce consistency where it is not appropriate.

## Decouple Coverage From Purpose

* Many people confuse the purpose of a test with its area of coverage
* As a result, people often write tests that are slower than they need to be, more difficult to maintain, and often report failures at a much broader level than they need to.
* Decide on purpose first, and let the purpose drive the choice of the format in which you capture the test.
* Business-oriented tests should be written in a language and format that allows teams to discuss potential problems with business domain experts.
* Once you've decided on the format and the purpose, think about the minimal area of coverage that would serve the purpose for that particular test. This will mostly be driven by the design of the underlying system.

## Avoid having Strict coverage targets

* Self explanatory

## Measure your tests' half-life

* Start measuring the half-life of your tests, that is, their stability.
* Practically this means measuring the amount of change within your tests and their associated underlying features.
* Use this data as an input to trigger analysis into why they are changing that much and whether a course of action is needed to address them
* For example, if the data points to brittle, intermittently failing and poorly written tests then maybe some investment is needed to refactor or rewrite the tests
* Having a measure of the stability of tests gives teams some really useful information with which to inspect and adapt their testing strategy.
* Instability gives an indication about areas of the system that might be riskier and requires further, more concentrated testing.
* Failing automated tests, that are immediately fixed without any deeper analysis, may mean that areas of weakness in the system are not identified quickly enough.
* Establish a reliable way of measuring the rate of change of tests (Eg, google docs sheet measuring the number of check-ins for each test)
* When you measure the number of changes and the interval between changes, you start to notice those tests that need the most maintenance.
* Also why not measure how many bugs get found by each test or feature?
* When a feature is not worked on and has become a stable feature of the product, the test which tests that feature should not change much
* Typically, you'll find the reason for test instability in one of these three reasons:
	* A volatile or evolving part of the system, often involving continued new feature requests, meaning new development and probably a fair amount of refactoring too
	* A weaker part of the solution, where more bugs are detected, possibly a part central to the design that is regularly changed or impacted by the addition of new features
	* The tests are fragile and need to be refactored

## Optimise for reading, not writing

* Focusing too much on how quickly tests are written leads to an instant sense of achievement but a horrible waste of time.
* There are just two moments when an automated test provides useful information: the first time it passes and when it subsequently fails.
* The first green bar on a test should reliably tell us that the feature is now there, and that is does what we want it to do.
* Subsequent test passes don't really require attention or action - when a test is passing nobody needs to do anything.
* If a test is not easy to understand, it's difficult to argue about completeness, so we won't be able to know for sure that our work is done when it passes for the first time.
* If a test is difficult to understand, and it doesn't clearly communicate its purpose, pinpointing problems is very difficult when it fails.
* Its far better to optimise tests for reading than for writing.
* Tailor the format, the language and the concepts used in a test to the primary reading audience.
* When a test is for a business rule or a business process, write it so that people who performing that process can understand it.
* Write technical tests so that developer can find their way around them quickly.
* In business-oriented tests, if you need to compromise either ease of maintenance or readability, keep readability.

## Name Tests For Search Engine Optimising

* Generic test names make it incredibly difficult to identify existing tests that correspond to proposed feature changes.
* This significantly increases the maintenance costs of larger systems.
* Generic names are a wasted opportunity to provide a navigation guide through a large test suite.
* Because there is no easy way to discover relevant tests for a feature, testers and developers have to read the contents of individual scenarios to understand potential changes. This is time consuming and error prone.
* Good test names are specific, and they pinpoint the purpose of the test or the scenario.
* Think of test names as keywords for quick discovery
* Imagine that the test was an online document and that you were looking for it using a search engine.
* A good heuristic for naming tests is to imagine a hierarchical navigation through the test suite, then collect all the names of the modules that would lead to a particular test.
* Add to that name whatever makes a particular test specific or different from the other tests int he same group.
* Avoid using conjunctions (and, or, not..) in test name. These are a sign that a test is doing too much

## Explain the purpose of a test in the introduction


....



## Split Just-In-Case tests from Key Examples

* Having separate specification documents that reuse the same automation allows teams to do assisted exploratory testing and quickly try out lots of different additional scenarios, even keeping them in a regression test suite if needed.

## Let The Chaos Monkey out Periodically

* Technical code coverage is relatively easy to measure, but it doesn't actually say much about the effectiveness of a test system.
* Risk coverage theoretically gives much better measurement of effectiveness, but it is also a lot more difficult to measure.
* A good set of tests should warn about unexpected impacts and prevent function regression problems.
* The best way to check if it will serve that purpose is to actually cause problems and see if the tests catch them.
* You can do this by running tests without the internet on for example
* Occasionally throw in undesirable conditions for your tests.
* Do the pass even though they should not?
* This approach allows you to periodically cause artificial crises in a safe environment, so they can improve their processes without having to put out fires at the same time.
* Think of these "chaos monkey" sessions just as a type of exploratory testing activity that requires the involvement of a slightly larger, more cross-functional, group.
