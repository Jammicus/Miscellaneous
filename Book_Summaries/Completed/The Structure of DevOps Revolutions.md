# The Structure of DevOps Revolutions

Speaker: Mike Long

* Agile = theory, Devops =practice
* Don’t be the first or last to adopt a technology or methodology, try pick it up in the middle


- - - -

# CI/CD for Humans

* Give ownership to devs for deploying -> Have trust in them
* Feature firewall -> New features hidden behind flags, these are turned on when they have been tested/are ready
* Engineer Presence -> You change it, you deploy it

- - - -

# Effective Leadership in Agile/DevOps Environments

* Is there a need for leaders if a team is autonomous and self-reliant?
	* Speaker believes there should be leaders still, and will explain why.
* Leadership can be expressed & shown at any level
* Leaders lead other people (Professionals).
	* Do we see ourselves are professionals? 
	* Do we have discipline 
* When leading others, we only see what they do, their behaviour and their knowledge.
	* Underneither, there is their thoughts, their views, the ambitions ….
* Teams contain multiple professionals with the following factors: 
	*  A level of maturity -> How long they have worked as a team and their strengths and weaknesses 
	* They can be autonomous -> Do they have a level of responsibility that gives them the sense of autonomous. 
	* a level of trust -> A sense of “them” vs “us” -> 
* The company consist of core values, culture, and mission.
	* These reflect what the company wants to happen and what not to happen.
	* Values are what we believe in 
	* Culture grows organically -> But you should set guidelines for what you expect (Eg, that others should learn).
	* Mission -> What are we working for? This can be broken down from company to Mission for each team. 

## Leadership Styles and Theories

* Shouting/Yelling at others -> Sign of lost control.
* Directive leadership -> Goal oriented. Sets enforced ways. Problem is that it does not inspire others.
* Participative leadership -> 
	* Least participative -> Decides solution without team input
	* Most participative -> Designates the decision to the team, and they come up with the solutions
* Salvant leadership: 
	* Listen to your team
	* Have empathy towards your team members.
	* Stewardship over a product
	* Persuade, rather than demand.
	* Make others aware of their environment 
	* Conceptualize the big picture and understanding why you and your team is there -> and explain this to the team.
	* Heal wounds in the team (Relationships between team members and teams)
	* Building community 
* Situational leadership model:
	* Directing -> Coaching -> supporting -> delegating
		* These move on based on the followers competence and your level of trust in them
	* (High directive, low participative) -> (Low directive, low participative)

## Leaders and Managers

* Becoming a manager does not make you a leader. 
* Leaders should be selected -> not chosen as they have the rank

## Attitude 

* They have  a certain attitude, but also as level of aptitude 
* If you want to lead somebody, the first crucial step is leading yourself

## Effective Leadership

* Effective leaders enable the team to reach their full potential 
* They set the stage -> They remove obstacles whether physical of mental so their team can progress 
* Give the team space to grow and experiment 

## Important leadership traits.

* Leading by example
* Integrity 
* Empathy
* Visible -> There inside/with the team. Being approachable to others
* Responsible 
* Adaptable
* Information is motivation -> Give the team the full picture as to why we are doing X
* Decisive -> The worst decision you can make its not making a decision within a time frame
* Be Vulnerable -> Show others that you are just like them.
* Get out of the way -> Let them do the important work.

## Leaders and modern software delivery teams

* Crazy amount of challenges for leadership
* Do small steps as a team
* Ensure your team has a high level of maturity.
* Leadership of multiple levels is key
* Show up when things are starting to go wrong
* Get things done
* Take charge (Your technical proficiency, yourself, your team)
* Remember to add value to your team.
* Experiment different leadership styles for your team 
* Find your own style of leadership

## Two books to read:

* Turn the ship around
* Team of Teams 


- - - -

# Continuous Delivery With Jenkins: the Good, the Bad and the Ugly


## Plugins

* `stats.jenkins.io` is useful to check the health of plugins before downloading them

## Requirements on  a CI/CD platform

* Run on premise
* Infrastructure as code
* Customisable
* Scalable
* Isolated builds using containers
* good pipeline visualisation

## Pipelines in Jenkins

* Traditional jobs with a chained as downstream dependencies
* JobDSL
* Jenkinspipelines plugin suite/Jenkinsfile. (Recommended way of doing it nowadays)
	* Good -> Has groovy at hand, can write it as a langauge.
	* Bad -> Debugging it is a nightmare. No builtin way to re-run failing stages of the build (Have to re-run from scratch)

## Visualisation 

* Important for fostering fast feedback loops
* Delivery pipeline plugin is a more detailed version of blue ocean.

## Jenkinsfile

* You can use shared groovy libraries for all your Jenkins files.
	* You should do this for shared thing (Eg, git permissions, versioning, etc)
	* You should store in a git repo, which is checked out for specific builds (Loaded implicitly)
* Your jenkins files should be easy to adopt.
* Use docker to build all the projects, so they can select their own tools.

## Making Upgrades easier

* You should treat your Jenkins code as software that goes through the build -> test -> release process.
* Checkout container-testing 


- - - -
# Continuous Delivery Patterns for Modern Architecture

* Modern Architecture -> More about technical leadership.
* All requirements (Functional/non functional) need to be in your pipeline.

## Continuous Delivery

* Producing valuable & robust software in short cycles
* Optimising for feedback and learning (Fast feedback, quick learning times)

## Business Needs 

* Velocity (Fast to market) Stability (Robust software)
* Continuous delivery is achieved when stability & speed can satisfy business demand
* Discontinuous delivery occurs when stability and speed are not there

## Core challenges with modern java architecture

* With the introduction of micro services, it introduces more pipelines.
* Each of these pipelines should be independent of each other. 
	* This allows us to move pipelines at different rates (Independent service deployment)

##  Architecture 101

* Within each monolith, theres many domains which contain many layers and many modules components frameworks and libraries(Eg liberator, transformer, and their components )

## Coupling Cohesion continuous delivrry

* 99% problems come from highly coupled loose cohesion
* Remember to have your software as low coupling high cohesion 

## Testing triangle

* You should have a triangle with the following as most tests to minimum:
	* Unit (most)
	* integration
	* component
	* End to end
	* Exploratory (Least)


## Functional testing: End-to-end

* Can be a great scaffolding for building software.
* Design your software via contracts (What you will give).
	* Think about using BDD as well
* Make basic happy paths/high level tests that you use when building (IE, adding items to your cart)

## Contracts

* API = service contracts
* Look into consumer-driven contracts 

## Messaging Contracts

* Any payload within a message is an implicit contract 
* Message schema’s are APIs
* Look into kafka 

## Contract Verification

* Used when you make a change, to see whether you will break anything else.
* This may not be worth the cost -> Startups and small/medium enterprises are not ideal candidates for this
* Use choreography  or orchestration-> This is verifying behaviour (interactions) vs verifying state 

## Testing Non functional requirements in the build pipeline
* Architecture quality -> SonarQube / Code Climate
* Performance and Load testing -> Gatling/ Locust / Bees with m’guns
* Security testing -> OWAPSP dependency check / bdd-security / Docker Bench for Security / CoreOS Clair


- - - -

# Providing and Supporting Docker images

> Docker: The worlds most heavily funded college project  

## “Official” Docker hub.

* Official images are chosen by docker inc - this may not actually be the organisations repo

## Custom Registry 

* Own custom registries are considerably faster and more reliable than docker hub. 
* This also gives you the chance to get metrics on who is pulling your images.
* Very easy to set up.

## Problems from having own registry

* Some people only want to use docker hub for some reason
* Some tooling may break as its only configured for docker hub (Automated builds / kitematic)
* China -> With the great firewall, the docker hub has a usable mirror, whereas custom registries are stuck behind the firewall. 

## Base Images

* Some times some products (Such as Node JS) are not supported on alpine. 
* Its important to choose base images that support your dependancies. 
* Elastic search guys use CentOS7. 
* Think about what your customers use, and use that (Eg, caplin should use centOS7)
* Each image they provide has:
	* Similar setup
	* Shared Layers
	* JVM Size
	* Bugs 
* Think about how often you will be creating new images -> If very often, size is important, if not often, size is not the main concern, stability is (EG liberator is not released often -> Use centOS as we have tested it against CentOS rather than alpine)
* Size is however important when stateful and stateless are issues
* Think about having different flavours of images (Eg, Base/Minimal, OpenSource, Different Operating systems, Full features) (Think about keeping the same base image for each however)
* Think about different JDK versions -> Try keep it uniform across all images.
* Remember, the container should not change any permissions (EG, on persistent volumes) which are not within the container!!

## Release Policy

* NEVER use latest -> Always use a fixed version. Depending on when you start and run a container, you may have different “Latests”
* Do not use Major.Minor versions -> Different minors may cause issues moving container between nodes on failover. This could be an edge case, but this should be considered.
* Tagging is also a problem -> If you find a container is “Bad” , and you have to fix it, you will have a different “build” time to other components.
	* don’t need to worry if you do not release a “stack” of software. 

## Running as Root

* Don’t do it, it can cause security issues.
* Ideally, create a user for your application and run it as that

## Mode

* Assumes that you need to support two types of mode:
	* Production -> Used in a cluster
	* Development -> Ran locally on your machine
		* These may have different code
* Env var which turns on and off config depending on modes?

## Default Credentials

* Ideally, you should set environment variables for credentials for the first occurrence on the container being ran. 
* Baking in credentials is terrible for security issues.
* Think about certificates -> Try not to make them in, but rather make it so the user can generate it when the container is ran for the first time

## Support

* Don’t mutate the bind mounted local directory
* You and your team need to understand linux base images (Eg, ULimit size in our container)
* There are leaky abstractions with docker -> Replicating bugs will involve you running OS and docker versions the same as the bug finder to try reproduce it.
* Think about helm and kubernutes for your container
	* This will be hard -> You will have to test cluster OS/Setting permutations


