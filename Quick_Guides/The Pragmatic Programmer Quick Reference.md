# The Pragmatic Programmer Quick Reference


1. Care about your craft
2. Think about your work
3. Provide options, not excuses
4. Dont live with broken windows, fix these when you see them
5. Be a catalyst for change
6. Remember the big picture
7. Make quality a requirement issue
8. Invest in your knowledge portfolio
9. Critically analyze what you read and hear
10. Its both what you say and how you say it
11. Dont repeat yourself
12. Make it easy to reuse
13. Eliminate effects between unrelated things
14. Nothing is cast in stone
15. Use tracer bullets to test something
16. Protothype to learn
17. Program close to the problem domain, design and write code in your customers language
18. Estimate 
19. Iterate the schedule with the code
20. Keep knowledge in plain text
21. Use command shells 
22. Learn a single editor and use it well
23. Always use source control
24. Fix the problem rather than blaming
25. Take deep breathes and debug slowly
26. Very rare to find bugs outside the application, search your application well
27. Dont assume, prove instead
28. Learn a text manipilation language
29. Write code that produces code (Code generators)
30. It is impossible to write perfect software
31. Use contracts to ensure your code does only as it is supposed to do
32. Crash rather than letting it run with errors/exceptions
33. Uses assertions to prove your assumtions
34. Uses exceptions for only exceptional things
35. Finish what you start
36. Keep modules as independant of each other as possible (Low Coupling)
37. Configure, dont integrate
38. Put the details in meta data, and make the code abstract
39. Analyze the workflow, what tasks are reliant on each other, and what tasks can be done in parrallel
40. Design interms of services
41. Design your program for concurrency
42. Seperate views and models
43. Use blackboards to coordinate workflow
44. Rely on reliable things
45. Estimate the complexity of your algorithms
46. Test your estimates
47. Refactor early and often
48. Design your code so it can be tested
49. Test the software regularly
50. Dont use wizards that you dont understand
51. Dig for requirements, enquire as deep as you can
52. Work with a user to think like a user
53. Abstractions are better than implementations
54. Use a project glossary ( A source file with specific terms and vocabulary in the project)
55. Ask if someone must be done this way, what other ways can it be done?
56. Start the project when you feel ready
57. Do it rather than describe it
58. Dont be a slave to formal methods
59. Costly tools dont produce better products
60. Organize your team around functionality
61. Automate as much as you can
62. Test early,often and automatically
63. Code is not finished till tests pass
64. Introduce bugs to check that your tests work correctly, then remove the bugs when the tests have proved that they are correct
65. Test the state of the program, not your code coverage
66. Find and fix a bug once. 
67. Engish is also a programing language, write documents how you would write code
68. Contain your build documentation with your code
69. Gently exceed the expectations
70. Sign your work. Your work is a reflection of yourself

## CheckList
* To maintain orthogonaliy:
	* Design independant components
	* Keep code decoupled
	* Avoid global data
	* Refactor 
* Architectural Questions:
	* Are resonsibilities defined?
	* Are collaborations defined?
	* Is coupling minimized
	* Where can we reduce duplication
	* Can modules access data when needed
* Debugging checklist:
	* Is the problem from a bug, or is this a symptom?
	* If you explained the problem to a colleague, what would you say?
	* Have I ran the code through tests with different data?
	* Do the conditions that caused this bug exist somewhere else in the system
* The Law of Demeter for Functions
	* Objects methods should call only methods belonging to:
		* Itself
		* Any parameters passed in
		* Objects it creates
		* Component objects
		
* How to Program
	* Stay aware of what you are doing
	* Dont code blindfolded
	* Follow a plan
	* Rely on trust worthy things
	* Document assumptions
	* Test assumptions
	* Prioritize your efforts
