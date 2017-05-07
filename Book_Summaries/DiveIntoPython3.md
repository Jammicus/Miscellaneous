# Dive Into Python 3 

---------------

[Amazon Link](https://www.amazon.co.uk/Dive-Into-Python-Pilgrim-2009-07-31/dp/B01JXTT234/ref=sr_1_2?ie=UTF8&qid=1494148748&sr=8-2&keywords=dive+into+python+3)

------

## Your First Python Program

### Declaring Functions

``` def functionName(para1,para2...): ```

* Def must be used to define a function
* Arguments are seperated with a comma
* Phython does not define a return type or whether they even return a value
* If there is a return statement, it will return that value, which is ` None` or some sort of object
* Functions end with a colon, not semi colon

#### Optional & Named Arguments

* You can assign default values to arguments
* You do this in the the function defintion

``` def functionName(x=100,y=True): ```

* If you define a value to an argument in the method declaration, this is called and **Optinal parameter**
* If you do not give it a parameter or overwrite this value, it will use the value you defined.

### Calling A function

* ` functionName(Paras)`


### The Import Search Path

* Python looks in several places when you try to import a module. Specifically, in all directorie defined in ` sys.path`
* To import this, type ` import sys`

### Everything is an object

* Functions are technically an object
* Functions can have attributes which are available to you at runtime
* To access a modules functions, you use the syntax `module.function()`


### Indenting Code

* Python does not use curly braces
* Instead it uses indentation to tell what the body of methods are
* If statements do not have brackets around the expression that is evaluated
* For/if statements end with: after the expression
* Carriage returns are used to seperate statements, and colons and indentation to seperate code blocks (Java uses semicolons for statements and curly braces for code blocks)


Example :


```
def approximate_size(size, a_kilobyle_is_1024=true):
	if size < 0:
		ExecuteCodeHere
	else 
		doSomethingElseHere


	for x < y:
		do something
```

### Exceptions

* Python encourages exceptions that you have to handle
* Unhandled exceptions are when the Python shell prints some details and how it happened.
* Handled exceptions have code that will do something when the exception is thrown
* Python does not declare exceptions that could be thrown on methods like java does.Its up to you to decided what exceptions to catch
* Python uses ` try...except` to handle exceptions, and ` raise` to generate them. The java equivlents are `try..catch` and ` throw `
 
 Example:
 
 ```
  if size < 0 : 
 		raise ValueError('This is not big enough')
 ```	

* Functions that raise it do not have to handle it.
* If an exception is not delt with in the function that raised it, it is passed to the function who called it, then the function who called that and so on until it reaches the top of the stack.
* If your exception is NEVER handled, your program will crash!

### Catching Import Errors

*  ` Import Error` is a build in exception
*  These are raised when you attempt to import a module but it fails
*  Generally this happens as the module is not in the class path or when there are two modules implement a common api but one is more desirable than other. 
* You can try to import a module, and if that does not work, you can try to import another

Example:

```
try :
	from lxml import etree
except ImportError:
	import xml.etree.ElementTree as etree
	
```

### Unbound Variables

* Python will not let you reference a variable which does not have a value
* If you do, you will get ` NameError: name 'x' is not defined `


### Case Sensitivity

* Everything in Python is case- sensitive, such as function names, class names, variables...

### Running Scripts

* Modules are objects 
*  ` if __name__ == '__main__'` is the first thing ran in a python program (Equivilent to javas main method)
*  `__name__` depends on how you are using the module, If you are importing a module, then `__name__` will bw the modules file name, without a directory path or file extension
*  If running a module as a stand alone program, `__name__` will be the default value `__main__`.


------

## Native Data Types

### Basic Types

* Remember each type is a objects, python does not have primitive types.
* Every value has a data type
* You do not need to declare the datatype of a varibale.
* Native basic types are:
	* Booleans
	* Numbers (This includes integers, floats, fractions and complex numbers)
	* Strings
	* Byes & byte arrays (Eg, a image file)
	* Lists (These are ordered)
	* Tuples (Orders immutable sequences of values)
	* Sets (Unordered values)
	* Dictionaries (Key-value, unordered)

### Booleans

* True or False
* Python expects expressions to evaluate to booleans (Areas where this occurs are called a boolean conext)
* Due to legacy code, True can equal 1, and false can equal 0 (Eg, true + true = 2)

### Numbers 

* Supports both integers and floats, (No doubles)
* You can use `type(x)` to check the type of that variable
* Can also use `isintance(variable,type)` to check whether it is a certain type
* Adding a int to a float will result in a float

#### Integers to floats and floats to integers
 * To change a integer to a float: ` float(x) `
 * To change a float to a integer ` int(x) ` 

#### Common Numerical Operations

* `/`
* `//` (rounds down)
* `+`
* `-`
* `**` (x power of y)
* `%` modulo (Remainder)

#### Fractions

* Need to `import fractions`
* to create a fraction: ` x = fractions.Fraction(y,z)`
* When you do math operations on a fraction, it returns a new fractions object
* Python will not create a fraction with a zero denominator

#### Numbers As Booleans

* non-Zero integers are true, zero is false
* Non-zero floats are true, 0.0 is false 
* Fractions with a numerator of 0 are treated as false, no matter what denominator

### Lists

* Like arraylists in Java (No fixed size, holds objects ect...)


#### Creating a list

* Use square brackets and commas to seperate its members

` ourList = ['a','b','c','hello] `

* Accessing member of a list, you pass the index

`ourList[1] = 'b' `

* You can traverse back from the end of the list, to do this, you pass a negative value

`ourList[-2] = 'c' `

* Last item of a list is always treated as -1


#### Slicing A List

* Slicing a list splits the list and returns a new list from the split
* To split: ` x[start:end]
* This will include the start and end elements
* You can pass negative numbers
* If you do not define a start, or end, it will assume for start you want it to start from the first element, and end from the last element

#### Adding To a List

* Four ways:
	* ` x + [y,z] `
	* `x.append(x)`
	* `x.extend([y,z])`
	* `x.insert(index,value)`

#### Searching Values in A List

* `count` can be used to return the number of occurances of a member

Example

`x.count(y)`

* `in` returns true if a element is in the list

Example

`y in a_list `

* `index` is used to return the index of a member if it exists

Example

` x.index(y)`

#### Removing Items From A List

* ` del ` removes the item at a specified index or by value

Example

`del x[2]`
`del x['hello']`

* After a deletion, items are shifted towards the front of the list if need be.

* Lists can use the standard pop and push operators
* Pop will return the value at the specified index

Example

`x.pop()`
`x.pop(2)`

#### Lists as Booleans

* Empty list is false
* Lists with >= 1 item are true, values are irrelevant


### Tuples

* Tuples cannot be changed once created
* Created using brackets

Example

` ourTuple = ("a","j","k")`

* You can slice a tuple
* Accessing members is done in the same mannor as you would for a list
* You cannot add/remove elements from a tuple once its created
* You can use the `in` operator to check members of the tuple
* Tuples are faster than lists, and considered safer as you cannot change them
* You can convert a tuple into list with `tuple()`
* You can convert a list to a tiple with `list()`

#### Tuples as Booleans

* Empty tuple is false
* Tuple with at least one item is true, no matter what the value



### Sets

* Can only contain values of immutable datatypes
* When you have two sets, you can use the standard set operators such as `set difference ` `union`....
* Sets are unordered

#### Creating a set

* use curly braces
* sets are implemented as classes
* You can create empty sets, but do not use curly braces, as this will create a dictonary (due to legacy code....)


Example

` ourSet = {1,2,3} `

* To create a list from a set, use `set()` 


#### Modifying A Set 

* Two possible ways : `ourSet.add(x)` or `ourSet.update[z,a,b])`
* Add adds a single element, update adds multiple`


#### Removing Items From A Set

* Two possible ways: ` ourSet.discard(x)` or `ourSet.remove(x)`
* If a value does not exist and you use `discard`, nothing will happen
* If a value does not exist and you use `remove`, an error will be thrown
* Sets also have `pop`
* To remove all elements from a set, use `ourSet.clear()`
* Trying to pop a empty set will result in an error


#### Common Set Operations

* `value in ourSet`
* `ourSet.intersection(anotherSet)` (in both ourSet and anotherSet)
* `ourSet.difference(anotherSet)` (In ourSet, but not anotherSet)
* `ourSet.symmetric_difference(anotherSet)` (Returns a new set that contains all the elements that are in exactly one set)
* `ourSet.issubset(anotherSet)` will return a True or False
* `ourSet.issuperset(anotherSet)` will return True or False

#### Sets In A Boolean Context

* Empty sets are treated as false
* Any set with at least one item is true, value of that item is irrelevant

### Dictionaries

* Unordered key-value pairs. 
* If you add a key, you must add a value.
* You can not have duplicate keys
* When assignining a new value to an old key, it will replace the old value
* Getting the number of keys in a dictonary can be done with `ourDictionary.len()`

#### Creating Dictionaries

• ` ourDictionary = { 'key1':'value1', 'key2':'value2'} `

#### Modifying A Dictionary

* `ourDictionary['newKey']='newValue'`

#### Mixed-Value Dictionaries

* Dictionaries can hold any datatype
* Within a dictionary, you can has as many types as you like
* Keys can only be strings, integers and a few other types
* Values do not have to be the same type as their key

#### Dictionaries as Booleans

* Empty dictionaries are treated as false
* Otherwise the dictionary is treated as true

### None

* None is treated as a null value
* This is not the same as 0, false, ect
* None has it own data type
* You can only assign none to data types
* All variables that have none assigned to them are equal

---------------

## Comprehensions

### Working with Files & Directories

* the `os` module has a considerable amount of resources for getting information and manipiulating files, directories,processes and venvironment variables.

#### Current Working Directory.

* Current working directory is a invisible property that is constantly stored in Pytho memory
* No matter what you are doing, there is always a current working directory.
* the `os` module has two functions for dealing with the current working directory?:
	* `os.getcwd()` gets the current working directory
	* `os.chdir('filePath')` changes the current working directory
		* You should use a linux style file path, this will work on windows

#### Working With Filenames And Directory Names

* `os.path` module contains functions for manipulating filenames and directory names

#### Listing Directories

* `glob` module can be used to easily get the contents of a directory programmatically.
* Takes wildcards and returns lists of files that meet the wild card

Example::

```
import glob
glob.glob('examples/*.xml')

```
* Above, `'examples/*.xml'` is the wild card

#### Getting File Metadata

* Meta data is information about the file, such as creation date, last-modified date, file size and so on
* Can get this info using `ourMetaData=os.stat('fileName'`
* You can then use other functions on `ourMetaData` such as time to get the information

#### Constructing Absolute Pathnames

* Use the `os.path.realpath()`

### List Comprehensions

* Provides a way of mapping a list to another list by applying a function to each elements of the list
* This results in a new list, leaving the old list intact

* ` ourNewList = [whatToDo for whatToDo in ourNewList]`

Example:

`ourNewList = [elem * 2 for elem in ourNewList]`

* This works by the interpreter looping through and assigning each variable to elem, then, the elem is multiplied by 2, then added back into ourNewList
* You can use an if statement to filter results that should/shouldnot be changed.

Example

` [elem * 2 for elem in ourNewList if elem < 10]`
* The if statement is checked after elem has been multiplied by 2 If the resulting elem is less than 10, it will be in the new list, otherwise it is disguarded 

### Dictionary Comprehensions

* Same as list comprehension, but it makes a new dictionary rather than a list
* Has the same principles as used in list comprehension

### Set Comprehensions

* Can take a set as an input and populate that set
* Can contain an if clause to filter each item before returning the result set


------–-----

## Strings

### String basics

* Every bit of text is stored in a particular character encoding
* This provides a mapping between the stuff you see on your screen and the stuff you computer stores in memory and on disk.
* There are many different character encodings.
* Characters can be in multiple encodings, but, each encoding may use a different sequence of bytes to store these in memory


### Unicode

* System designed to represent every chracter from every language
* Represents each character as a 4-byte number (UTF-32)
* Characters that are used in multiple languages generally share the same number
* UTF-16 is a subset of UTF 32, it uses the most popular characters from UTF32
* UTF-16 is more efficient than UTF 32 due to the fact is uses 2 bytes per char instead of 4 bytes of 32
* UTF-8 is currently the latest standard and by default python uses this

### Creating Strings 

* ` ourString = "Hello world"`

### Formatting Strings

* Can use `ourString.format()`
* Some other useufl methods:
	* index()
	* find()
	* split()
	* count()
	* replace()
	
------

## Regular Expressions 

* A standardized way of searching, replacing, and parsing test with complex patterns of characters.
* YOu can even embed comments within regular expressions

### QuickIntro

* `^` Matches the start of a string
* `$` Matches the end of a string
* `?` Makes a given pattern optional
* `|` Is OR

Example

```
pattern = '^M?M?M(CM|CD|D?C?C?C?)$'
```

### {N,M} Syntax

* {N,M} Matches all the characters in a range

Example 

`pattern = '^M{0,3}$`

* This matches m0,m1,m2,m3


### Sumary

* `^` matches the beginning of a string
* `$` matches the end of a string
* `\b` matches a word boundary
* `\d` matches any numeric digit
* `\D\` matches any non numeric character
* `x?` matches an optional x character (in other words, matches x zero or one times)
* `x*` matches x zero or one times
* `x+` matches x one or more times
* `x{n,m}` matches x to the all possible elements between n and m
* `(a|b|c)` matches a or b or c
* `(x)` is a remembered group. Can get the value of what matched by using `groups()` method of a object return by `re.search`
* `[xyz]` is either x or y or z, but only one of them
* `re.sub()` performs regular expression based string substitutions

-------

## Closures & Generators 

### Basics

* Need to use the `re` module

Example:

```
re.sub('$','es',noun)
```
* this adds ES to the end of noun

```
 re.sub('y$','ies','vacancy')
```
* This transforms words ending in y to words ending in ies

* This works by defining a condition to match, then what to do when that condition is patch (Pattern matching)

### A List of Functions

* you have to define all posible rules as functions.
* You then use the `rules` keyword, with `(conditionToMatch,whatToApply)`
* YOu then use a if statement to apply it.


Example:

```
import re

def match_sxz(noun):
	return re.search('[sxz]$,noun)
	
def apply_sxz(noun):
	return re.sub('$','es',noun)
	
def match_h(noun):
	return re.search('[^aeioudgkprt]h$',noun)

def apply_h(noun):
	return re.sub('$','es',noun)
	
rules = ((match_sxz, apply_sxz),
			(match_h, apply_h))

def plural(noun):
	for matches_rule, apply_rule in rules:
	if matches_rule(noun):
		return apply_rule(noun)
```

* Each mathc rule has its own function, whcih calls the results of `re.search()`
* Each apply rule has its own function that calls `re.sub()`
* the `rules` data structure is used, which is a pair of functions
* Using a for loop, you pull out the match and applies rules from the `rules` structure.
* The first iteration matches the first set of match and apply, then the second iteration applies the second match and apply, and so on.
* The `rules` data structure contains function objects, not names of functions. 
* `Rules` variable can be seen as a sequence of pairs of functions
* This terminates as soon as thereis a match (I think)

### A List of Patterns

* You can create a function that creates a new function

Example:

```

import re

def build_match_and_apply_functions(pattern, search, replace) :
	def matches_rule(word):
		return re.search(pattern, word)
	def apply_rule(word):
		return re.sub(search, replace,word)
	return (matches, apply_rule)
```

* Each def in this function is a rule
* You return the rules 
* You then pass the relevent parameters and it will apply the rules to each of these parameters
* 
------

## Classes & Iterators 

### Defining Classes

* As Python is object-oriented, you can define classes, inhert and instantiate classes
* Syntax is `class OurClass: `
* Everything inside a class must be indented

Example

``` 
class OurClass:
	pass
```

* Pass statement is like curly brackets in java.
* use this when you dont want to implement the class yet

#### `__init___()` method

* This is called as soon as an instance of the class is created. 
* This is not a constructor
* This always referes to the current instance of the class
* Init can take arguments
* You should assign each of these arguments to self.
* self represents the current object (This in Java)

Example

``` 
class Fib:
	def __init__(self, max):
		self.max = max
```

### Instantiating Classes

* You call the class as if it was a function, while passing the arguments that `__init__()` requires.
* Syntax for this is ` variable = importName.ClassName(parametersForInitMethod)`

Example

```
import fibonacci2
fib = fibonacci2.Fib(100)
fib

```

* the third line creates the instance of the class, with the value of fibonacci2.fib(100)

### Instance Variables

* Variables that are specific to one class
* Each of these variables can have seperate values for each class instanization
* `max` in the below example is an instance variable

Example:

```
def __init__(self, max):
	self.max = max

def __next__(self):
	fib=self.a
	if fib> self.max:

```



### Fibonacci Iterator

* Iterators are classes that define `__iter__()` method

Example

```
class Fib:
	def __init__(self, max):
		self.max = max
	
	def__iter__(self):
		self.a = 0
		self.b = 1
		return self
	def__next__(self):
		fib = self.a
		if(fib > self.max)
			raise StopIteration
		self.a, self.b = self.b, self.a + self.b
		return fib
```
* Building iterations from scratch, you must you a class rather than a function
* Calling `Fib(max)` creates the instance of the class, which calls `__init__()`
* `__iter__()` method is called whenever anyone calls `iter(fib)`
* `__next__()` is called when someone calls next() on the class instance
* 


------

## Advanced Iterators TODO


----

## Unit Testing

* Writing unit tests before you write a piece of code is good practice (TDD)
* Unit tests make sure that you do not over code. Then all test cases pass, a function is complete
* When refactoring, unit tests help make sure that your function works in the way it was intended
* Having a good set of tests helps prevent your code from breaking someone elses code

### A single Question

* Each test case should answer a single question about the code it is testing
* Each test should be able to:
	* Run by itself, without human input
	* Determine by itself whether a function it has tested has passed or failed the test, without humans interpreting the results
	* Run in isolation, separate from other test cases.

Example:

```
import roman1
import unittest

class KnownVlaues(unittest.TestCase):
	known_values = ( (1, 'I'),
						(2, 'II'),
						(3, 'III'),
						(4, 'IV'),
						(5, 'v'))
	
	def test_to_roman_known_values(self):
		for integer, numeral in self.known_values:
			result = roman1.to_roman(integer)
			self.assertEqual(numeral, result)
			
	if __name__ == '__main__'
		unittest.main()
		
```

* You must sublcass the `TestCase` class of the `unittest` module
* Every individual test is its own method. 
* Test methods take no parameters, and return no values, and must have a name beginning with `test`
* Running ` unittest.main()` runes each test case.

### Halt

* You tests must also fail when given a bad input instead of a god input.
* You can assert that an exception is thrown when a bad error is done


----------

## Files

### Reading From Text Files

* To open a file, do the following:

` ourFile = open( 'folder/lname.type', encoding='utf-8')

* Python has a build in `open()` function
* Directories use `/`. This works on all operating systems
* Directory path does not begin with a slash or a drive letter, so its a relative path
* The encoding is platform dependant. Becareful waht encoding you use.
* If you need the default character encoding, import `locale` module and call `locale.getpreferredencoding()`

### Stream Objects
* `open()` returns a string object, which has its own methods and attributes

Example

```
ourFile = open(x,encoding='utf-8')

ourFile.name

ourFile.mode

ourFile.encoding

```


### Reading Data from A text file

* after opening use `ourFile.read()`, this will get all the text and return a string
* Empty files will return an empty string
* `read()` read can take a parameter than defines how many characters should be returned
* `.tell()` 
* `.seak(x)` moves you to the x byte of the file
* You can then read from there, or do other operations (Think of it as a pointer to part of the file)

### Closing Files

* You should close files as soon as you are finished with them, as keeping files open consumes a considerbale amount of memory
* This is done by `ourFile.close()`
* `ourFile` object will still exist, but you cannot read from it anymore.


### Reading Data One line at a time

* Lines are seperated by enter
* Line ending are delt with automatically by python

Example:

```
line_number = 0

with open('folder/file.type', encoding='utf-8') as a_fiie:
	for a_line in a_file:
		line_number+= 1
		printsomethinghere
		
```

* with open will automatically close files
* use for loops to read a line at a time.


### Writing To Text Files

* Open and then start writing.
* You need to pass `mode='w'` into the open() function
* `append` mode will add data to the end of the file, this is done by pass `mode='a'` to the `open()` function
* Either of these will create the file automatically if the file does nto exist
* Remember to close the file as soon as you are done
* to write into the file, use `ourFile.write('abcdef')`

### Standard Input, Output , and Error

* Have to use the `sys` module
* Same as java
* Basic exmaple: `sys.stdoout.write('haha')`


----------------------
## XML (TODO)

### Crash Course

* Used to describe hierarchical structured data
* XML document contains one or more elements, which have a start and end tags

Example:

```
<hello>

</hello>
```

* Can have nested elements
* Elements can have attributes, which must be `name=values`
* Elements can aslo have text

Example:

```
<foo lang='en'>
Hello world
</foo>

```


-------

## HTTP Web Services (TODO)
* Python 3 comes with two libraries for interacting with HTTP webservices:
	* `http.client` - Low level libary that implements  RFC 2616
	* `urllib.request` - Abstraction layer built ontop of `http.client`
* You should not use either of these, the open source library `httplib2`

### Features of HTTP

* Caching - Minimizing the need to request data from another source
* Last Modified Checking - When you request data for the first time, the server can send back a `last-modified` header. 
	* This will tell you when the page was lst modified
	* When accessing it again, you can send a `if-modified-since` header with the request. If the data has changed, the new data is sent back with a `200 status code`. If it hasnt changed, data is not sent.
* ETag Checking -  alternative way of doing `if-modified-since`
* Compression -  Way to reducing the size of the data sent
	* Can do this using `gzip` or `deflate`
	* Can ask the server to send the data in a compressed format
	* Done by using a `Accept-Encoding` header stating what compression algorithms you support.
	* If the server supports the same compression algorithm, will send the data using that compression algorithm
* Redirects - If a website changes its URL, it allows you to redirect from the old URL to the new URL


---

## Packaging Python Libraries 

* Python comes with a packaging framework called `Distutils`
* It integrates with the python Package Index, which is a central repository for open source Python Libraries
* You need to ensure you have a root directory where everything that your python script will need is in.
* A readme file should be included.

### Writing Your Setup Script

* The Distutils setup script should do as little as possible.
* The more exotic your installation process is, the more exotic your bug reports will be.
* the first line must be `from distutils.core import setup`
* The `setup()` function must take named arguements for every parameter. This is a hard requirement.
* The following named arguements are required for `setup()`
	* name - the name of the package
	* version - the version number of the package
	* author - your full name
	* author_email - your email address
	* url - home page of your project. (This can be your PyPI package page if you do not have a homepage
* The following can be including in the setup script, but are not required:
	* description - one line summary of the project
	* long_description
	* classified - a list of specially formatted strings

Example of the stup method:

```
from distutils.core import setup
setup(
	name = 'test project',
	packages = ['testProject'],
	version = '1.0.2',
	description = 'This is our test project'
	author = 'James'
	)
```
	
### Classifying Your Package

* Classifiers are used for others to search and find your package
* These are tags that are used in search engines
* Classifiers are optional, but you should include at least three classifiers
* The three classifiers you should include are:
	* Programming Language. This should include ` Programming Language :: Python ` and ` Programming Language :: Python :: 3`
	* Licence
	* Operating System - Does it only run on Windows? Or can it run on multiple platforms
* The following classifiers are recommended, but not essential:
	* Development status - Alpha, beta? Complete?
	* Intended Aucdience -  Desktop users? Science/research, developers?
	* Framework - Django, zope?
	* Topic

Example 

```
Programming Language :: Python
License :: OSI approved :: BSD License
Operating System :: OS Independent
Development Status :: 5 - Production/Stable
Environment :: Web Environment
Framework :: Django
Intended Audience :: Developers
Topic :: Internet :: WWW/HTTP
Topic :: Internet :: WWW/HTTP :: Dynamic Content
Topic :: Internet :: WWW/HTTP :: WSGI
Topic :: Software Development :: Libraries :: Python Modules
```


### Specifying Additional Files With a Manifest

* Distutils by default will include the following in your release package:
	* README.text
	* setup.py
	* .py files needed by the multi-file modules listed in the packages parameter
	* Individual .py files listed in the py_modules parameter
* The default manifest file is called  `MANIFEST.in` 
* The commands in a manifest file allows you to include or exclude specific files and directories.
* You should only include a manifest file if you do not want to include all files in your directory

### Cheking Your Setup Script For Errors
* In the command line, the following will check that your script is okay:

``` 
YourPackage.exe check running check
```

### Creating A Source Distribution

* By minimum, you should build a source disribution that contains your source code, your Distutils setup script, your readMe file, and needed additonal files
* TO do this, pass `sdist` command to your setup script

Example:

```
yourPackage.exe setup.py sdist
```
### Creating A Graphic Installer

* To upload software to the Python Package Index requires you to do the following:
	* Register yourself
	* Register your software
	* Upload the packages you created with `setup.py sdist` and ` setup.py bdist_*`




-------

## Porting Code To Python 3 with 2to3 (TODO)

--------

## Special Method Names (TODO)

----

## Iterators

This is taken from 
[StackOverflow](http://stackoverflow.com/questions/9884132/what-exactly-are-pythons-iterator-iterable-and-iteration-protocols)

An ITERABLE is:

* anything that can be looped over (i.e. you can loop over a string or file) or
* anything that can appear on the right-side of a for-loop:  `for x in iterable: ...` or
* anything you can call with `iter()` that will return an ITERATOR:  `iter(obj)` or
* an object that defines `__iter__ `that returns a fresh ITERATOR, or it may have a `__getitem__` method suitable for indexed lookup.


An ITERATOR is an object:

* with state that remembers where it is during iteration,
* with a `__next__`method that:
	* returns the next value in the iteration
	* updates the state to point at the next value
	* signals when it is done by raising `StopIteration`
* and that is self-iterable (meaning that it has an `__iter__` method that returns `self`).

Notes:

The `__next__` method in Python 3 is spelt next in Python 2, and
The builtin function `next()` calls that method on the object passed to it.