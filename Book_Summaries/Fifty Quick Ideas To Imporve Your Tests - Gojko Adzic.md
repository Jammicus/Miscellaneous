# Fifty Quick Ideas To Imporve Your Tests - Gojko Adzic


-------------------------


# Generating Test Ideas

* Software quality pyramid:
	* DOes it work? What are the key features, key technical qualities
	* Does it work well? What are the key performance, security, scalabiity aspects
	* Is it usable? What are they key usabuility scenarios?
	* Is it useful? What production metrics will show that it is used in real work?
	* Is it successful? What business metrics will show that this was worth doing? Is it operating within financial constraints?

## Explore capabilities, not features

* Story-oriented exploratory testing sessions lead to tunnel vision and prevent teams from getting the most out of their effort
* Exploritory testing is most powerful when it deals with the unexpected and the unknwon. 
* Testing cant be focused purely on features
* Good ways to look for unexpected risks is not to explore features, but releated capabilities.
* Focusing on exploratory testing on capabilities instead of featurres leads to deeper insights and prevents tunnel vision
* Makethis work by focusing on the what the user has to do in order to do something, rather than what they want to do. 

## Start With Always/Never

* To paint the big picture quickly, start off with a ten-minute session on identifying things that should always happen, or should never happen
* This should not be done by a single person. Several groups should brainstorm and then a list should be created from both

## Tap Into Your Emotions

* Having a heuristic for test design can stimulate some very useful discussions and upturn some stones that otherwise might have been left untouched.
* The heuristics proposed are based on nine emotions or types of behaviour (Remember this as ShadedFigs):
	* Scary
		* Areas of the highest risk to the stake holders
	* Happy
		* Simpliest path through the particular area of behaviour and functionality you can thing of. This is expected to pass everytime
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
		* Find the breaking point of the functions and components so you can see what scale of solution you currently have and give you projects for future changes in business volues
* To make this work : Start off doing the happy path, and look along it for alternatives

## Test Benefit as Well as Implementation

* You should describe your test through implementation details, rather than potential benefits
* You're looking for whether the implementation of the benefit is done well, rather than whether than the presence of that feature
* Instead of asking "does it work?", ask **"How would you know if it actually works well"**

## Quantify enen if you cannot measure

* Qualities that are hardly measured rarely get the testing attention they deserve (Eg, usability or performance)
* They are often inspected as an afterthought, typically when someone complains
* Just because something is difficult to test, we shouldn't give up on capturing or expressing expectations. 
* Even if you're not going to actively measure an important aspect of quality, try to quantify it
* Try to capture key representative scenarios that are good indicators of speed by working with the stake holders (Eg, instead of the homepage having to be "fast", select scenarios such as logging in, adding things to the basket, and try to quantify how fast each of these scenarios should be)

## Organise Test Ideas using an ACC Matrix

* Its hard to establish clear, impartial and objective criterion for how much testing is enough.
* Attribute-component-capability matrixes can be helpful here.
* It charts different capabilities in relation to system components and quality attributes.
* its a table in whcih columns have the names of quality attributes and system comonents are represented by rows
* Capabilities should be high leveled, and they should describe a whole rang eof scenarios.
* The guidelines for identifying capabilities:
	* Write a capability as an action, ideally from the sense of a user accomplishing some task
	* Provide enough information for a tester to understand what variables are involved in the related test cases, and do not aim to provide full details of the test cases
	* A capability should work together with other capabilities. Dont aim to describe a use case or a user story with a single capability.

## Use Risk Checklists For Cross-cutting Concerns

* These are where specific risks and concerns apply to a large set of things to test. 
* This often leads to a lot of repetition and routine work, regardless of whether the tests are automated or manual
* Instead of describing individual test scenarios : Try to name the key risks in global checklists
* This helps QA toexplore the right things, and prevents skipping critical risks. 
* These should be quick and simple steps that are easy to check

## Document Trust Boundaries

* With different teams, trust boundaries are contracts between teams as to how things should be. 
* You should explicitly identify and document trust boundaries as a group, including developers, testers and business take holders
* Identify how much you trust another team or vendor, and identify whether you need to test against them rigorusly, or can you test less firmly

## Monitor Trends In logs and consoles

* System logs and consoles are often the only reliable source of information about what really goes on in complex workflows or systems with many components.
* Having a good understanding of how a log should appear will help you identify changes, which could be good or bad, quickly

## Mob Your Test Sessions

* Have test sessions with various people
* Each person will have their own goals and ideas, helping you to find pain points or concerns
* Start with the scope and purpose of the session, and go from there
* Give everyone a idea of the requirements, the acceptance criteria, the design, the test environment and ata converns, the information objectives, and so on

## Don't let the pen be the bottleneck

* If there is a single pen beign wielded by one person, it can lead to bottle necks waiting for the person to do their part
* Everyone should be able to contribute, and have full visiblity of the process
* A good idea is to give everyone access to gogle documents, and allow them to comment on different aspects

## Snoop On The Competition

* When planning your testing activities, look at the compoetition for inspiration - The cheapest mistakes to fix are the ones already made by othe rpeople.
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

## Contrast Exmaples With Counter-Examples

* Counter examples are cases that show when the feature does not apply, or when the new behaviour is not invoked. 
* Example could be when there is not enough items in your shopping basket for an offer to apply
* To make it work, do the following in order:
	* Start with the simplest example you can think of that shows a scenario where the feature of business rule takes effect. Write scenarios for that
	* Underline the parts of the example that are most relevant to the feature or rule. Make sure you distinguish between inputs (eg, item type, currency) and outputs (free delivery) 
	* For each output, identify a different possible value this output could take.
	* Repeat until you have a valid and an invalid example 

## Describe What, Not How (Page 742(

	