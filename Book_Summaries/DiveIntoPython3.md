# Dive Into Python 3 


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
 
 ` if size < 0 : 
 		raise ValueError('This is not big enough')
 	
`

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

* /
* // (rounds down)
* +
* -
* `**` (x power of y)
* % modulo (Remainder)

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

## Regular Expressions TODO
-------

## Closures & Generators TODO

### Basics
s

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

Example
```
def __next__(self):
	fib=self.a
	if fib> self.max:

```

* max is an instance variable


### Fibonacci Iterator

* Iterators are classes that define `__iter__()` method