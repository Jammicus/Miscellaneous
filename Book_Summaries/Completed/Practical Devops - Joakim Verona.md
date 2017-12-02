# Practical Devops - Joakim Verona

**NOTE, VERY BASIC BOOK, DONT BOTHER READING IT IF YOU HAVE WORKED IN DEVOPS FOR MORE THAN A MONTH**
- - - -

## A View From Orbit

* DevOps process and Continuous Delivery pipelines can be very complex. 
* Will be covering the following:
	* Overview of the DevOps process, Continous delivery pipeline implementation, and participants in the process
	* Release Management
	* Scrum, Kanban, and the delivery pipeline
	* Bottlenecks
	
### The DevOps Process and Continuous Delivery - An Overview

* Example of a continuous delivery pipeline in a large organisation:

![](Practical%20Devops%20-%20Joakim%20Verona/Practical%20Devops%20-%20Joakim%20Verona/Screenshot%202017-11-25%2011.23.37.png)

* The developers work on their own workstations, and push to a repository when ready.
* The previous control system listens for code changes (Eg, a merge in git). It then runs tests , builds artefacts, and deploys the artefacts for the QA team
* The QA team does testing on these items, 
* Once the QA team is happy, it is passed along to the operation team at releases it or in some pipelines, deploys it 
* Bottle necks are things in the pipeline that prevent moving onto the next stage, such as:
	* Failing automated tests
	* Build and deploy errors
	* Massive changes that require the production and test environments to be altered 

## How DevOps Affects Architecture

* Will be covering:
	* Aspects of software architecture and what it means to us while working with our DevOps glasses on
	* Basic terminology and goals
	* Anti-patterns, such as the monolith
	* The fundamental principle of the separation of concerns
	* Three-tier systems and micro services

### Introducing Software Architecture

* There are two man scenarios that Devops engineers need to solve for Continuous Delivery to be successful:
	* We need to be able to deploy small changes often
	* We need to be able to have great confidence in the quality of our changes

### The Monolithic Scenario

* When your dependancies are tightly linked together. It makes continuous delivery painful
* For example, if you just have to change a typo - it would result in your whole system being built, which could take hours.

### Architecture rules of thumb

* Separate your concerns - You should consider different aspects of the system separately. Keep things as single units that you can combine together, rather than ONE massive thing
* Think of the principle of cohesion -> Have strong cohesion, where everything inside a module/ unit links together. 
* Have low coupling - Where there is two modules are not highly dependant on each other.

## Everything as Code

* Version control is a must.
* There are various branching strategies, This a common one used by teams:

![](Practical%20Devops%20-%20Joakim%20Verona/Practical%20Devops%20-%20Joakim%20Verona/Screenshot%202017-11-25%2011.48.49.png)

### Artefact Version Naming

* The basic principles of version naming:
	* Version numbers should grow monotonically (be come larger)
	* They should be comparable to each other, and it should be easy to see which version is newer
	* Use the same scheme for all your artifacts
* These normally translate into a version number having three/four parts:
	* First part -> Major
	* Second part -> Minor changes, which are backward API compatible
	* Third part -> Bug fixes
	* Fourth part -> Build number

## Building the Code

* Your automated system needs to build the code into artefacts or into local binaries to run tests against
* There are many different types of build tools (Gradle, npm…)
* The principle use of your automated system is to build new artefacts as soon as changes have been detected
* Continous integration builds artefacts, but does not release/deploy them once built and tested. 
* Continuous Delivery automatically deploys/releases the artefacts  once built and tested

### Build Triggers


* There are various ways to trigger your automated builds:
	* Rolling the repository for changes.
	* Nightly builds that run at a set time
	* A build that is triggered from another build passing
	* Tokens, that are sent to the build server to trigger the build based on a condition you set.

## Testing the code

* Ideally, you want robust, automated tests that you trust.
* Manual testing should still be done however, but only after the tests have passed / before being released

## Deploying code.

* Many different ways of deploying your code/ configuring your build machines. Here is a table with corresponding terminology:

![](Practical%20Devops%20-%20Joakim%20Verona/Practical%20Devops%20-%20Joakim%20Verona/Screenshot%202017-11-25%2012.01.43.png)

* Try building it with a language that is as close to the language that the application is created in as possible.
* There are several cloud solutions as well:
	* AWS
	* Azure
	

## Monitoring the Code

* Several solutions, but graphite is the best .
* Not covering anything else


#Book

#Book/Devops
