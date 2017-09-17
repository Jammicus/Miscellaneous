# The Pragmatic Programmer - Andrew Hunt & David Thomas

-------
[Amazon Link](https://www.amazon.co.uk/Pragmatic-Programmer-Andrew-Hunt/dp/020161622X/ref=sr_1_1?s=books&ie=UTF8&qid=1494148529&sr=1-1&keywords=the+pragmatic+programmer)

-------

## A Pragmatic Philosophy

* Factors that distinguish a pragmatic programmer:
	* Attitude
	* Style
	* Philosophy of approaching problems and their solutions
	* Ability to think beyond the immediate problem by placing that problem in a larger context.
	* Responsibility for everything they do

### The Cat Ate My Source Code

* A pragmatic programmer takes charge of his career and is not afraid to admit ignorance or error
* When something goes wrong, you should provide options to rectify it, not lame excuses
* Do not blame someone or something else, this is completely your responsibility

### Software Entropy

* Refers to the amount of 'disorder' in a system
* When there is a high amount of entropy in a software project, we refer to it as `software rot`
* Entropy starts with small, little broken windows
* You should fix everything broken, no matter how small as soon as it is discovered (Bad designs, bad code, ect)
* this prevents more broken windows.
* Once one window is broken and its not fixed, a project will get worse very quickly
* Your code should always set a standard, no matter how bad other contributors code is

### Stone Soup and Boiled Eggs

* Sometimes, you have to go ahead and do something without the permission of others.
* Once you have implemented it show them, and say how we can move forward with this, or how you can improve it
* If you can add something to the project, do it
* Always remember the big picture. Will this add to the big picture, or is this  just a short term thing?

### Good Enough Software

* You should discipline yourself to write software that's good enough for your users, for future maintainers, for your own peace of mind.
* Good enough does not imply sloppy or poorly produced code.
* Users should be given the opportunity to participate in the process of deciding when what you've produced is good enough

### Involve Your Users in the Trade-Off

* Quality should be a requirements issue
* Most users would rathe ruse software with some rough edges today rather than wait a year for it
* Great software today is often preferable to perfect software tomorrow
* Give users something to play with early, and get their feedback

### Know When To Stop

* Don't spoil a perfectly good program by over embellishment and over-refinement.
* Move on and let your code stand in its own right for a while.
* Your program will never be perfect

## Your Knowledge Portfolio

### Knowledge Portfolio

* Managing your portfolio is like managing a financial portfolio.
* Technical and financial portfolios have the following aspects:
	* Serious investors invest regularly - as a habit
	* Diversification is the key to long-term success
	* Smart investors balance their portfolios between conservative and high-risk, high-reward investments
	* Investors try to buy low and sell high for maximum return
	* Portfolios should be reviewed and rebalanced periodically

### Building Your Portfolio

* To have a successful career, you must manage your portfolio using the following guidelines:
	* Invest Regularly
	* Diversify - The more different things you know, the more valuable are.
		* As a baseline, you need to know the ins and outs of the particular technology you are working with currently.
		* The more technologies you are comfortable with, the better you will be able to adjust to change
	* Manage risk - Its not ideal to put all your effort into high risk technology. Diversify and invest is various technologies.
	* Buy low, sell high - Learning a young technology before it gets popular can be very rewarding
	* Review and rebalance - You need to keep on track of changes to the technologies you know

### Goals

* The best way to acquire intellectual capital to fund your portfolio:
	* Learn at least one new programming language every year
	* Read a technical book each quarter
		* Ideally read a book each month.
	* Read nontechnical books too - Remember that computers are used by people, people whose needs you are trying to satyisfy
	* Take classes
	* Participate in local user groups
		* Find out what people are working on outside of your company
	* Experiment with different environments
		* If you use Windows at work, try using Linux at home
	* Stay current - Subscribe to trade magazines and other journals. Choose some that cover technology different from that of your current project
	* Get wired - Join newsgroups, understand jargon

### Critical Thinking

* You should critically think about the things you read and hear
* You need to ensure that the knowledge in your portfolio is accurate and unswayed by either vendor or media hype


### Communicate!

* Know what you want to say
* Know the audience you are talking too
* Choose a suitable moment to talk to people
* Adjust your communication to the audience
* Make what you are looking about look good
* Involve your audience
* Listen and take onboard the audiences feedback
* Its both what you say and the way you say it

## A Pragmatic Approach

### The Evils of Duplication

* Maintenance is not a discrete activity, but a routine part of the entire development process
* Every piece of knowledge must have a single, unambiguous, authoritative representation within a system
* Don't repeat yourself!

### How Does Duplication Arise?

* The following can cause duplication:
	* Imposed duplication : Developers feel there is no choice
	* Inadvertent duplication - Developers have not realized they are duplicating code
	* Impatient duplication - Developers get lazy and duplicate code because it is easier
	* Inter-developer duplication - Multiple people on a team produce the same code

### Orthogonality

* Code should be orthogonal
* Two pieces of code are orthogonal if when one piece changes, the other does not have to change
* This has several benefits:
	* Eliminates effects between unrelated things
	* Promotes reuse
	* Diseased sections of code are isolated
	* Resulting system is more robust
	* Better testing as it is easier to design and run tests on its components
	* The product will be less tightly tied to a particular vendor, product or platform.

### Ways to Apply Orthogonality

* Organise your team into groups with well-defined responsibilities and minimal overlap
* Separate the infrastructure from the application
* Check your design by asking yourself "If I change this, what else will need to be changed?"
* Choose technology wisely.  Ask when adopting a technology whether this imposes new problems or challenges for your code that should not be there

### Coding For Orthogonality

* Keep your code decoupled
	* Write modules that do not reveal anything unnecessary to other modules, and modules that do not rely on other modules implementations
	* If you need to change a objects state, get that object to do it for you
* Avoid global data
	* Use parameters to pass data to objects
* Avoid similar functions


## Reversibility

* There are no financial decisions
* You should prepare your code for changes in requirements
* Think about your architecture and how will that deal with change

## Tracer Bullets

* Add little functionality to ensure things are working correctly (Firing tracer bullets to check that its meeting its goal)
* Regularly using tracer bullets allows you to adapt to new requirements
* Trader code approach has the following advantages:
	* Users get to see something working early
	* Developers build a structure to work in
	* You have an integration platform
	* You have something to demonstrate
	* You have a better feel for progress
* Tracer code is different to prototyping as tracer code is part of the final design. Prototyping produces code that is thrown away

## Prototypes and Post-it Notes

* Things to prototype:
	* Architecture
	* New functionality
	* Structure / Contents of external data
	* Third party tools or components
	* Performance issues
	* User interface design
* You should prototype to learn and gain a better understanding
* You should ignore the following when prototyping:
	* Correctness
	* Completeness
	* Robustness
	* Style
* When looking at the prototype architecture, look at the following:
	* Are the responsibilities of the major components well defined and appropriate?
	* Are the collaborations between major components well defined?
	* Is coupling minimized?
	* Can you identify potential sources of duplication?
	* Are interface definitions and constraints acceptable?
	* Does every module have an access path to the data it needs during execution? Does it have that access when it needs it?


## Domain Languages

* Always try to write code using the vocabulary of the application domain
* If you can, try to actually write code using the vocabulary and syntax of the language/domain
* Program close to the problem domain

### Implementing a Mini-Language

* Mini-language may be in a line - oriented, easily parsed format.
* If you need to implement a more complex language, you should implement it using BNF

### Data Languages and Imperative Languages

* Data Languages produce some form of data structure used by an application.
* These languages are used to represent configuration information
* Imperative languages build upon data languages  by adding contain statements and control constructs


## Estimating

* You should estimate to avoid surprises
* You should determine whether your users need a highly accurate estimate or a ball park figure
* Your estimates should be in the following categories;
	* Duration 1-15 Days = Estimate in days
	* Duration 3-8 Weeks = Estimate in weeks
	* Duration in 8-30 Weeks = Estimate in months
	* Duration in 30 + Weeks = Don't estimate
* To estimate, do the following steps:
	* Gather the requirements
	* Build a model
	* Break it into components
	* Assign each component to a time value
	* Sum the answers
* If a estimate is wrong, figure out why the estimate was wrong
* To estimate the project schedule, do the following:
	* Check the requirements
	* Analyze risk
	* Design, implement and integrate
	* Validate with the users
* You should iterate the schedule with the code
* If someone ask's you for a estimate, always say *I'll get back to you*

## Basic Tools

* Each tool will have its own personality and quirks.
* The better your tools, and the better you know how to use them, the more productive you can be.
* Keep all your knowledge in plain text, rather than binary
* You should use useful tags to group data
* Terminal commands are vital for quick development, learn them!
* Its better to use one editor well, than multiple poorly
* If you can, port your keybindings to different editors. Have a consistent series of commands that you use
* Your editor should have the following features:
	* Configurable
	* Extensible
	* Programmable

## Source Code Control

* Source control use is not an option, its mandatory


## Debugging

* Debugging is unavoidable, no matter how much you detest it
* Approach debugging as a puzzle to solve.
* When trying to recreate a bug, recreate the steps to find the bug
* You should brutally test both boundary conditions and realistic end-user usage patterns. You should do this systematically
* Avoid blaming others

### Debugging Strategies

* Visualize what your data is doing, what is its values? What state is the program in?
* Trace through the program (Break points)
* Rubber ducking - Explain the problem to someone else, including the steps and what you can prove so far
* Use process of elimination
* Never assume, instead, prove it.

## Text Manipulation

* Text manipulation can be noisy, messy and somewhat brute force
* You should learn at least one text manipulation language
* We use text manipulation languages every day, its vital to understand one (Such as SQL)

## Code Generators

* Code that writes code
* Passive code generators run once and produces as result
* These save typing and allow you to produce parameterized templates based on a set of inputs
* Uses of Passive code generators:
	* Creating new source files
	* Performing one-off conversions among programming languages
	* Producing lookup tables and other resources that are expensive to compute at runtime
* Active code generators are used each time a result is required
* Whenever you find yourself trying to get two disparate environments to work together, you should consider using active generators (Eg, taking a schema to produce something, when the schema changes, the produced thing should changed)

## Pragmatic Paranoia

* **You can never write perfect code**
* Pragmatic programmers program in defenses against their own mistakes
* Design by contract : Clients and suppliers must agree on rights and responsibilities
* Dead programs tell no lies : We want to make sure that no damage is done when working bugs out. Check things often and terminate the program if things go bad
* Assertive programming: Write code that actively verifies your assumptions
* Exceptions : These cause more harm than good if not done properly


## Design By Contract

* Contracts defines your rights and responsibilities, as well as the other parties.
* Focuses on documenting and agreeing to the rights and responsibilities of software modules to ensure program correctness
* A program is correct when it does no more and no less than it claims to do.
* Every function and method must do something before it starts something
* Each function and method should have:
	* Preconditions - What must be true for the routine to be called. Routines should never be called if a precondition is violated. Its the callers responsibility to pass good data
	* Postconditions - What the routine will do. The state after the routine has finished. What will terminate the routine
	* Class invariants - Class that ensures that the condition is always true from the callers perspective. The invariable may not hold while the routine is running, but it must hold once it has finished

## Dead Programs Tell No Lies

* If there is an error, something very, ver bad has happened.
* Try to crash your program as early as possible

### Crash, Dont tell

* Rather than saying that a error happened, Crash the program instead

##  Assertive Programming

* If it cant happen, use assertions to ensure that it wont.
* Never put code that must execute into assertions
* Dont use assertions in place of real error handling
* Turning off assertions when you deliver a program to production is like crossing a high wire without a net.

## When To Use Exceptions

* Exceptions should be thrown/raise when something happens that is excepted to happen
* Exceptions should be used for exception problems.
* Error handlers are routines that are called when an error is detected.
* You will want to use error handlers when using a language that does not have exceptions (Such as C)

## How To Balance Resources

* Always finish what you started
* An object or routine that allocates a resource should be responsible for deallocating it.
* When a routine needs more than one resource at a time, there are two suggestions for dealing with this:
	* Deallocate resources in the opposite order that in which you allocate them
	* When allocating the same set of resources in different places in your code, always allocate them in the same order. (This reduces the possibility of deadlock)


## Bend Or Break

* You should make every effort to write code that is as loose, and as flexible as possible.
* Otherwise code will quickly become outdated and useless
* You can achieve loose code measuring coupling
* Coupling is the dependencies among modules of code
* You should write as little code as possible

## Decoupling and the Law of Demeter

* Organize your code into modules and limit the interaction between them.
* If one module gets compromised and has to be replaced, the other modules should be able to carry on
* You should be care about how many other modules you interact with, and how you came to interact with them.
* When we ask for an object for a particular serve, we want the service to be performed on our behalf
* The law of Demeter for functions attempts to minimize coupling between modules.
* It prevents you from reach into an object to reach ANOTHER objects methods
* Any method of an object should call only methods belonging to:
	* Itself
	* Parameters passed to the method
	* Objects it created
	* Directly help component methods

## Meta Programming

* Meta data should be used to provide configuration options (Eg, what database to use)
* Metadata is any data that describes the application and how it should be run, what resources it should use ect...
* MetaData is typically accessed at runtime, not compile time
* You should put abstractions in code, and details in metadata
* The benefits of this:
	* Forces you to decouple your design, which results in a more flexible and adaptable program
	* Forces you to create a more robust, abstract design by deferring details.
	* Can customize the application without recompiling it
	* Metadata can be expressed in a manner thats much closer to the problem domain than a general - purpose programming language
	* May even be able to implement several different projects using the same application engine, but with different meta data


## Temporal Coupling

* Temporal coupling is about time.
* You should always write code which allows for concurrency and to think about decoupling any time or order dependencies (Eg, a must call b, then b must call c  would be bad!)
* By analyzing the workflow of your users, in what steps they do something, you can improve concurrency
* Can anything they do be performed in parallel?
* Design using services - independent, concurrent objects behind well-defined, stable, consistent interfaces

### Design for Concurrency

* Global and static variables must be protected from concurrent access
* Objects must always be in a valid state when they are called, and they can be called at the most awkward of times

## It's Just a View

* Events are a special message that says "something interesting just happened"
* Events should be used to signal changes in one object that some other object may be interested in
* This minimizes coupling between objects, the send of the event does not need to have any explicit knowledge of the receiver.
* This is were we can use publish and subscribe
	* Objects can subscribe to another object
	* If an object is subscribed to an object, and then when that object is changed it will publish that something has changed
* Model-view - controller should be used
	* The model contains the data itself, with operations to manipulate it.
	* The view is separate, it is used to display the data in various ways
	* The controller provides a way to provide the model with new data, and pass data from the model to the view

## While You are Coding

* Pragmatic Programmers think critically about all code, including our own
* We constantly see room for improvement in our programs and our designs
* Something that should be in the back of your mind when producing code is that someday you will have to test it

##Programming by Coincidence

* You should avoid programming by coincidence - relying on luck and accidental successes - in favor of programming deliberately
* You should know why your code is working in the way that it does

## Accidents of Implementation

* These are things that happen because thats the way the code is currently written
* The following reasons are why you should mess with code that is currently working:
	* It may not really be working - It might just look like it is
	* The boundary condition you rely on may be just an accident
	* Undocumented behavior may change with the next release of the library
	* Additional and unnecessary calls make your code slower
	* Additional calls also increase the risk of introducing new bugs of their own

## How to Program Deliberately

* Always be aware of what you are doing.
* Don't code blindfolded. Attempt to build an application you don't fully understand, or to use technology you aren't familiar with, is an invitation to be misled by coincidences
* Proceed from a plan, whether in your head or written down
* Rely only on reliable things
* Document your assumptions
* Don't just test your code, but test your assumptions as well.
* Prioritize your effort. Spend time on the important aspects.
* Don't be a slave to history. Don't let existing code dictate future code. All code can be replaced if it is no longer appropriate

## Algorithm Speed

* Measured by O() Notation
	* o(1) =  Constant time
	* o(log(n) = Logarithmic
	* o(n) = linear
	* o(n (log(n)) = Worse than linear, but not much worth
	* o(n^2) = Square law
	* o(n^3) = Cubic
	* o(C^N) Exponential

## Common Sense Estimation

* Can estimate the order of many algorithms using common sense
* Simple loops = o(n)
* Nested Loops  = o(N x M)
* Binary Chop = o(log(n))
* Divide and Conquer = o (n log (n))
* Combinatoric(permutations of things) = Very slow

* You should test your estimates!

## When You Should Refactor

* Duplication - You've found violations of the DRY principle
* Nonorthogonal design - You've discovered some code or design that oculd be made more orthogonal
* Outdated Knowledge - Things change, requirements drift
* Performance - Bad performance

* You should refactor early and often

## How To Refactor

* Dont try to refactor and add functionality at the same time
* Make sure you have good tests before you begin refactoring.
* Run the tests often as possible
* Take short, deliberate steps.

## Code Thats Easy to Test

* Unit tests should be used to test modules independently
* When unit testing you should think of testing against contract - We want to write test cases that a given unit honors its contract (What we expect it to do under each condition)

## Using Test Harnesses

* Test harnesses should include:
	* A standard way to specify setup and cleanup
	* A method for selecting individual tests or all available tests
	* A means of analyzing output for expected or unexpected results
	* A standardized form of failure reporting.

## Evil Wizards

* Dont use wizard code that you do not understand.

## Before The Project

* Requirements should not be gathered, you should dig for them

## Digging For Requirements

* The best way to gather requirements is to work with a user to think like a user.
* Sit with them, understand their workflow and their daily tasks.

## Solving Impossible Problems

* You must challenge any preconceived notations and evaluate whether or not they are real.
* The problem is finding the real constraints.
* When you have a intractable problem, enumerate all the possible avenues you have before you.
* Then go through the list and explain why a certain path cannot be taken. Are you sure? Can you PROVE it?

## There Must Be an easier way

* Ask yourself the following:
	* Is there an easier way?
	* Are you trying to solve the right problem, or have you been distracted by a peripheral technicality?
	* Why is this thing a problem?
	* What is it thats making it so hard to solve?
	* Does it have to be done this way?
	* Does it have to be done at all?

## Not Until You're Ready

* Great performers share a trait: They know when to start and when to wait.
* Start when you are ready, if you have a nagging voice when you sit down to type, listen to it.
* If you're unsure how to start, start by prototyping

## Circles and Arrows

* Dont be a slave to formal methods Expensive tools do not produce better designs

## Pragmatic Projects

* The most important factor in making project-level activities work consistently and reliably is to automate your procedures.
* Remember success is in the eye of the beholder

## Unibquitous Automation

* `Cron` is a superb automation tool
* Allows you to schedule unattended tasks to run periodically (Normally in the middle of the night)

## Build Automation

* Procedure that takes an empty directory and builds the project from scratch
* The steps for this are:
	* Check out the source code from the repository
	* Build the project from scratch
	* Create a distributable image
	* Run specified tests

## Final Builds

* May have different requirements than  the nightly builds
* If the project is compiled differently from earlier versions, you must test against this version all over again

## Ruthless Testing

* Test early
* Test often
* Test automatically
* Coding is not finished until all the tests run

## What to Test

* Unit testing
* Integration testing
* Validation and verification
* Resource exhaustion, errors, and recovery
* Performance Testing
* Usability Testing


## Great Expectations

* Gently exceed your users expectations
* Try to surprise your users. Not scare them, mind you, but delight them
* Some easy things that look good to the average user:
	* Balloon or ToolTip help
	* Keyboard shortcuts
	* Quick reference guide as a supplement to the user manual
	* Colorization
	* Log file analyzers
	* Automated installation
	* Tools for checking the integrity of the system
	* The ability to run multiple versions of the system for training
	* A splash screen customized for their organisations

## Pride and Prejudice

* Sign your work
* Code must be owned, this can be personal ownership or communal ownership of code
* Your signature should come to be recognized as an indicator of quality
* People should see your name on a piece of code and expect it to be solid, well written, tested and documented.
