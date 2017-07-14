# Python Crash Course - Eric Matthes


## Varibles & Simple Data types

### Strings

* Can be in either " "  or ' '
* Can change the case of a string by using `.upper()` or `.lower()`
* To Concatenate strings, use `string1 + string2`
* To add whilespace, use `\n` or `\t` in the string itself
* To remove whitespace from the front of a string, use `.lstrip()`, From the end use `.rstrip()`
* To change another type to a string, use `str(typeToChange)`

### Numbers

* Floats
* Integers

## Introducing Lists

* Uses `['x',y,z]`
* Can store different types in a list
* Index based, starting at 0
* To access a element: `listName[indexOfElement]`
* To modify element of a list: `listName[indexToChange] = valueToAdd`
* To add a element to the end of a list: `listName.append(valueToadd)`
* Insert Element into specific index: `listName.insert(index, elementToAdd)`
	* This will shift the elements to the right of the index you have inserted a value to
* Remove element from a list: `del listName[index]` or `listName.pop(index)`
* Removing the last element: `listName.pop()` 
* Removing item by value: `list.remove(valueToRemove)`
* Sorting a list: `listName.sort()`
* Reverse sorting a list: `listname.sort(reverse=True)`
* Temporarily sort a list: `sorted(listName)`
* Reversing a list: `listName.reverse()`
	* This reverses the ordering, it does not sort then reverse!
* Finding length of a list: `len(listName)`
* Accessing the last element of a list: `listName[-1]`

## Working With Lists
* Looping through a list: 
```
magicians = ['alice', 'david', 'carolina'] 
for magician in magicians:	 print(magician)
```
* Looping the a range of values:

```for value in range(1,5):    print(value)
```

* TO make a list of numbers in a range: `list(range(1,6))`
* Making a list that skips numbers: `list(range(start,end,differenceBetweenNumbers)`
* Finding minimum value of a list: `min(listName)`
* Finding maximum value of a list: `max(listName)`
* Finding the total of a list: `sum(listName)`
* Slicing a list: `listName[startIndex:endIndex]`
* Slicing a list without knowing the end index: `listName[startIndex:]`
* Copying a list:

```
my_foods = ['pizza', 'falafel', 'carrot cake'] 
friend_foods = my_foods[:]
```

### Tuples

* Defining a tuple: `name= (x,y)
* Accessing the first element of a tuple: `name[0]`
* Accessing the second element of a tuple: `name[1]`
* Looping through a tuple:

```
for item in tuple:
	print(item)
```
* Overwriting a tuple: `oldTuple = (newXValue,newYValue)`
## If Statements

* Simple if: 

```
if x > 10:
	do something
```

* Checking for Equality:

```
if (x == y):
	do something
```

* Ignoring case:

```
>> car = 'Audi'
# This temporarily lowers the case, not perminantly!>>> car.lower() == 'audi'True
>>> car
'Audi'
```

* Checking for inequality:

```
if x != y:
	do something
```

* Checking multiple conditions with 'and'

```
if (x == y) and (y ==z):
	do something
```
* Checking multiple conditions with 'or'

```
if (x==y) or (y==z):
	do something
```

* Checking a value is in a list: ` 10 in listName`
* Checking a value is not in a list: `10 not in listName`
* if else: 

```
if  x > y:
	do something
else: 
	do something else	
```
* else if conditional (elif):

```
if  x > y:
	do something
elif x > y:
	do do something	
else: 
	do something else

```

* Checking if a list is empty:

```
if listName:
	do something
else:
	print("List is empty")	
```

## Dictionaries

* Key:Value pairs
* Dictionary creation: `dictionaryName = {'key1':Value1, 'key2':value2}
	* Can hold different types
* Empty dictionary creation: `dictionaryName = {}`
* Accessing Values in a dictionary: `dictionaryName['key']`
* Adding new key:value pairs: `dictionaryName['keyToAdd'] = valueToAdd`
* Modifying values in a dictionary: `dictionaryName['key'] = ourNewValue
* Removing key:value pairs: `del dictionaryName['keyToRemove']`
* Looping through a dictionarys key:value pairs:

```
for key,value in listName.items():
	do something
```

* Looping Through all the keys in a Dictionary:

```
for key in dictionaryName.keys():
	do something
```

* Looping through a dictionary keys in order:

```
for keys in sorted(dictionaryName.keys()):
	do something
```

* Looping through all values in a dictionary: 

```
for value in dictionaryName.values():
	do something
```

* Looping through unique valules in a dictionary:

```
for ourValue in set(dictionaryName.values()):
	do something
```

## User Input and While Loops
* Getting user input: `variableName = input("The user will see this text")`
* Converting input to an int: ` age =  int(input("Age please"))`
* While loop syntax:

```
current_number = 1while current_number <= 5:          print(current_number)          current_number += 1
```

## Functions

* Defining a function:

```
def functionName(parameter1,parameter2):
	do something
```
* Calling a function: ` functionName(value1,value2)`
* Setting a default value for a parameter (keyword argument)
	* not if the user does not supply a new value for this argument when the function is called, it will use the defined one:

```
def functionName =(argumentOne, argumentTwo = 20):
	do something
```

* Returning values:

```
def add (numberOne, numberTwo):
	return numberOne + numberTwo
```

* Making a parameter optional (you need to pass it a empty value): 

```
def optionalParameters(mustHavePara, anotherMustHavePara, optionalPara=''):
	do something
```

* Preventing a function from modifying a list (use slice, as it makes a copy of the original list)

```
def fuctionName(slicedList[:])
```

* Passing an arbitary number of arguments:
	* Note, thjis will make a tuple and pack all values it recieves into that tuple
	
```
def functionName (*tupleWithArguments):
	do something
```

* Mixing required and Arbitary Arguments:
	* the arbitary argument parameter must be at the end
	
```
def functionName(requiredParaOne, requiredParaTwo, *arbitaryPara):
	do something
```

## Classes

* Defing a class:

```
class ClassName():
	methods and variabls here
```

* Defining a class' constructor (called automatically when a new instance is made):

```
class ClassName():
	
	def __init__(self, para1,parat2):
		self.para1 = para1;
		self.para2 = para2;
```

* Creating a class in python 2.7(Have to pass 'object' to it):

```
class ClassName(object):
	do something
```

* Making an instance of a class:
	* paras are the parameters needed by the `__init__` method
	
```
ourVariable = ClassName(para1,para2)
```

* Making a method, rather than a function: `def methodName(self,parameters):`

* Accessing the Classes attributes: ` instanceVariable.attribute`
* Calling a classes methods: `instanceVairable.methodName(parameters)`
* Creating multiple instances:

```
instanceOne = ClassName()
instanceTwo = ClassName()
```

* Setting a default value for an attribute:
	
```
def __init__(self)
	self.defaultValue = 10
```

* Modifying an attributes value
	* Directly: ` instance.attribute = value`
	* Through a method 

``` 
def ourMethod(self, variableValue):
	self.attribute = variableValue

instanceVairble.ourMethod(newValue)
```

* Inheriting a class:

```

def childClass(ParentClass):
	def __init__(self,x,y,z):
	#State that the variables should be passed to the parent class
	super().__init__(x,y,x)

```

* Defining Attributes and Methods for the Child Class:

```
class childClass(ParentClass):
	
	def __init__(self, parentAttribute):
		super().__init__(parentAttribute)
		# Attribute for the child class
		self.childAttribute = 10;
		
	# Child Class method
	
	def childMethod(self):
		do something
```

* Overriding parent classes methods in the child class is done by defining the same method (With name!) in the child class
* Importing a class:`from variable import ClassToImport`
* Importing an Entire Module:  `import moduleName`
* Importing all Classes from a Module: `from moduleName import * `


## Files and Exceptions

* Reading files:
```
with open('textFile.txt') as file_object:
	contents = file_object.read()
	print(contents)
```

* Reading Line by Line

```
filename = 'textFile.txt'

with open(filename) as file_object:
	for line in file_object:
		print(line)
```

* Making a list of Lines from a File:

```
filename = 'textFile.txt'

with open(filename) as file_object:
	lines = file_object.readlines()
	
for line in lines:
	print(line.rstrip())`

```

* Working with a Files' Contents

```
filename = 'textFile.txt'

with open(filename) as file_object:
	lines = file_object.readlines()

# Add all the lines to a string
pi_string = ''	
for line in lines:
	pi_string += line.rstrip()
	
print (pi_string)
print(len(pi_string))
```

* Writing to an empty file:

```
filename = 'fileName.txt'

# 'w' for write mode, 'r' for read mode
with open(filename,'w') as file_object:
	file_object.write("Your text here")
```

* Writing multiple lines to a file(Write on seperate lines!):

```
filename = 'programming.txt'with open(filename, 'w') as file_object:    file_object.write("I love programming.\n")    file_object.write("I love creating new games.\n")
```

* Appending to a file:
	* Open the file in append mode then write

```
#Opening the file in append mode
with open(filename, 'a') as file_object:		file_object.write("I also love finding meaning in large datasets.\n")       		
        file_object.write("I love creating apps that can run in a browser.\n")
```

 * Try - except blocks
 	* same as try catch in java
 	* In the bewlo code, `Exception` can be changed to a speicifc exception, such as ZeroDivisonError

 ```
 try:
 	code that may throw exception here
 except Exception
 	do something with the exception
 
 ```
 
* Else blocks can be used in try except blocks. 
	* code that depends on the try block executing will go into the else block if successful

```
try:
	code here

except Exception:
	exception code here

else:
	code to execute if try was successful
		
```


## Testing Your Code

* Unit tests can be made from importing the `unittest` module
* Test cases are a collection of unit tests which demonstrate that the programs behaviour is correct
* To create a test class, you need to pass `unittest.TestCase` as a parameter to the class
* Asserts should be used in your test to return whether a test passes or not.
* Test methods should start with `test_`
* To test a specific class, import that class to the test class 

Example

```
import unittestfrom name_function import get_formatted_nameclass NamesTestCase(unittest.TestCase): """Tests for 'name_function.py'."""    def test_first_last_name(self):        """Do names like 'Janis Joplin' work?"""        formatted_name = get_formatted_name('janis', 'joplin')        self.assertEqual(formatted_name, 'Janis Joplin')unittest.main()
```

* `Setup()` methods can be used to ensure objects have values before the test is executed
