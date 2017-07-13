# Automate The Borign Stuff With Python - Al Sweigart

-------

## Python Basics

### Math Operators (Highest to lowest precedence)

*  `**` (Exponent)
*  `%` (Modulus/remainder)
*  `//` (Integer division/floorered quotient)
*  `/` (Divison)
*  `*` (Multiplication)
*  `-` (Subtraction)
*  `+` (Addition)

### Variables

* Can only be one word
* Can only use letters, numbers and _
* Cannot begin with a number
* Are case sensitive

### Boolean Operators

#### Binary Boolean Operators

* ` x and y`
* ` x or y`
* ` not x`
* `x==y`



### Flow Control

#### If Statements
* IF statmeents have the form of `if x == y:

Eg

```
if name == 'Alive':
	print('Hi, Alice.')
else:
	print ('Hello, stranger.')	
	
```
**Remember indentation**

#### Elif statements
* `elif` is an else if statement that will match even if the if before has been matched. 
* Below is a elif statement that will match against name, and then check age.

```
if name == 'Alice':
	print('Hi, Alice')
elif age <12:
	print('You are not a kid Alice')
```

* if you have multiple `elif`, it will only match once then terminate, rather than checking against each `elif`

```
if name == 'Alice'
	print('Hi, Alice.')
elif age < 12:
	print('You are not Alice, kiddo')
elif age > 2000:
	print('Something)'
elif age >100 :
	print('something else')		

```
#### While

* while statement continue till a condition is met.
* Make sure to ensure that the loop will terminate!
* **Remember indentation and colon!**

```
spam = 0
while spam < 5:
	print('hello world')
	spam = spam +1
```

#### Break
* If you place a break in the while loop body, it will exit the loop 

```
while True:
	print('Please type your name.')
	name =  input()
	if name == 'your name':
		break
print('Thanks!')
```

#### Contiune
* Continue statements are also used inside loops. When the program hits a contiue statement, it heads straight to the start of the loop and reevaluates the loops condition

Example

```
while True:
	print('Who are you?')
	name = input()
	if name != 'Joe':
		contiue
	password = input()
	if password == 'swordfish':
		break
print ('Access granted')
	
```

Here the loop continues until the name joe is entered, If joe enters the wrong password, then the loop will go to the beginning

#### Truthy & Falsey
* Some values are equivilent to true and false (known as truthy values)
* Examples:
	* `''` == falase
	* `0` == false
	* `0.0` == false
	* Everything else == true

#### For Loops
* For loops use in and range to know when to terminate and what starting value to have
* For loops use `range()` to get values

Example

```
for i in range(12,16):
	print(i)
```
this will print 12,13,14,15

* Range can be called with up to 3 values
* `range(startValue,endValue,valueModifier)`

Example

```
for i in range(5,-1,-1)
	print(i)
```
This will decrement everytime by -1
--
### Importing Modules

#### Import Keyword
* Uses:
	* Import keyword
	* The name of the module
	* Or optionally, multiple module names seperated by commas

```
import random
for i in range(5):
	print(random.randint(1,10))
```

```
import random, sys, os, math
```
#### From Keyword

* You can also use `from` keyword
* This will prevent the need to use to module name at the start of a method call
* The full name however makes it easier to read

```
from random
for i in range(5):
	print(randint(1,10))
```
--
### Functions

#### def Statement with parameters

* To create a function, you use the `def` keyword, followed by the name, then parameters, then definition

```
def hello(name):
	print('Hello' + name)
```

#### Return values and return statements

* `return` allows you to return a value when a value/expression is placed after it

```
def getAnswer(answerNumber)
	return answerNumber
number= getAnswer(5)
print(number)
```

#### The None Value

* Has no value.
* Functions that do not return anything return None by default
* None must start with a capital 

#### Keyword Arguments and Print()

* Keyword arguments are identifed by the keyword put before them in the function call
* Often used for optional parameters
* Print has an optional keyword arugment called sep, that is printed inbetween prints
* More will be taught later

```
print('cats', 'dogs', 'mice', sep=',')

```
this will return: cats,dogs,mice

#### Local and Global Scope

* Parameters are variables that are defined a functions declaration/body are "local" variables
* They can only be used inside that function
* Global variables (That are declared outside of a fucntion) can be used anywhere. 
* Functions can access global variables without having to pass them to the function

Example of local variable

```
def spam():
	eggs = 31337
print(eggs)
```
* Eggs is only created once the method has been called
* Eggs is destroyed as soon as the function has finished

Example of global variable

```
eggs = 31337
def printSpam():
	print(eggs)
```
##### Global and Local variables with the same name

* Try to avoid using local variables that have the same name as a global variable or another local varaible
* Technically it is legal to do this however

##### The Global Statement

* If you need to modifiy a global variable within a funciton, use the global statement
* If you have `global variableName` inside of a function, it says that the function refers to that global variable, so do not change it)

``` 
def spam():
	global eggs
	eggs = 'spam'
eggs = 'global eggs'
spam()
print(eggs)
```

The final print will print `spam`
This is because when spam is called, it will assign the global variable eggs to 'spam' ( As we have defined it as `global` in the function declaration)

Example

```
def spam():
	global eggs
	eggs = 'spam' # this is global
	
def bacon():
	eggs = 'bacon' # this is local
	
```

* If you ever want to modify the value stored in a global variable from in a function, you must use a global statement on that variable

#### Exception Handling

* Can be handled with `try` and `expect` statements
* You can put code that may cause an error in the `try` block
* Then you can handle the error in the `expect` block
	* `expect` needs to have the error in its definiton


Example

```
def spam(divideBy):
	return 42/divideBy
	
try: 
	print(spam(2))
	print(spam(12))
	print(spam(1))
	print(spam(0))
except ZeroDivisonError:
	print("Error: Invalid argument.')
	
```
--
### Lists

#### List Data Type

* Lists are a variable that can store multiple values **in an ordered sequence**
* Lists can contain different types (Eg, integers and strings)
* These are seperated by commas
* Lists are defined within brackets []
* Items in a list are called `items`
* Lists are assigned names, but the items inside a list are not assigned names, but rather indexes (Positions in a list)

Example
```
spam =[1,2,3]
```
#### Indexs
* To get an item from the list, use `listName[index]`
* lists start at index 0
* Negative indexes start from the end of the list

Example

```
spam = [1,2,3]
spam[2] == 2
spam[-1] == 3
```

#### Getting Sublists with Slices

* Slcie can get several values from a list in the form of a new list
* Slice is defined as `listName[startIndex:endIndex]`
* You can leave the startIndex or endIndex out, and python will assume it starts at the beginning/end respectively
* If you leave startIndex and endIndex out, it will assume to get the whole list

#### Getting a Lists length with len()

* len(listName) will return the number of items in a list

#### Changing Values in a list with indexs

* you can change the value at a lists index by `listName[index]=newValue`

#### Removing Values from Lists with del Statements

* `del listName[index]` will remove the value from the list
* Items will then get shifted to the left to fill the position that was removed

#### Working With Lists

* Its good practice to use while/for statements to add values to lists rather than defining loads of variables and adding them manually
* You do this by `listName +[valueToAdd]`

```
catNames[]
while True:
	name = input()
	if name == '':
		break
	# Add name to list
	catNames = catNames+ [name]
	
```

#### Using for loops with lists

* For loops will go through lists from start to end, then terminate
* Best to do this using range and len

Example

```
supplies = ['pens', 'staplers','flame-throwsers','binders']
for i in range(len(supplies)):
	print('Index' + str(i) + in supplies is : '+supplies[i])
	
```

#### The in and not in Operators

* Can detmine whether a item is in a list using `in` and `not in`

```
'howdy' in ['hello', 'hi', 'howdy', 'heyas'] 
Truespam = ['hello', 'hi', 'howdy', 'heyas']'cat' in spamFalse'howdy' not in spam 
False'cat' not in spam 
True
```

#### Methods

* Same as a function, but is called on a value.
* has the syntax `value.methodName(Parameters)`

#### adding values to lists using append() and insert()

* append is used to add a value to the end of the list

` listOne.append(value)`

* insert places a value at a specified index

`listOne.insert(index,value)`

#### Removing values from a list with remove()

* rempove takes a value, and if that value is in the list removes it
* if its not in a list, it will throw an error!

`listOne.remove(valueToRemove)`

#### Sorting the Values in a List with the Sort() Method

* sorts from lowest to highest, or alphabetically
* Lists which contain different types **CANNOT** be sorted
* Sort uses "ASCIIbetical" order. This means for a list with upper and lower case characters, it will sort by uppercase and alphabetically first, then lowercase and alphabetically (ABCabc)

`listToSort.sort()`

* Can use the parameter `reverse=True` to sort it from highest to lowest / reverse alphabetically

` listToSort.sort(reverse=True)`


#### List like types: Strings and Tuples

* Tuples and strings are treated as lists
* methods that can be used on lists can be used on these types

#### Mutable and Immutable Data types

* Lists are mutable (Can be added, removed or changed)
* Strings are immutable (Cannot be changed)
* When using methods that change values on immutable types, it simply creates a new varaibale of that type and assigns the value to it

#### Tuple Data Type

* Almost identical to the list data type.
* Are surronded by ()
* Seperated by ,
* If it only has one item in a tuple, should have , behind taht value
* Tuples are immutable

#### Converting Types with the list() and tuple() Functions

* list() and tuple() will return list versions of tuples and tuple versions of list respectively

--
### Dictionaries and Structuring Data

#### Dictionary Data Type

* Uses key:value pairs
* You call the key to get the value
* Keys can be strings or integers

Example

```
myCat= {'size':'fat', 'color':'grey'}
myCat['size'
'fat'
```

#### Dictionaries vs. Lists

* Dictionaries are unordered, lists are order
* There are no indexes
* Lists are only equal to each other if they contain the same vaues AND are ordered, dictionaries are equal only if they contain the same values
* Dictionaries cannot be sliced


#### The keys(), values(), and items() methods

* These can be used in for loops
* values() will return values in a list

```
 spam = {'color': 'red', 'age': 42} 
 for v in spam.values():	print(v)
```
This will return red and 42

* Keys will return keys in a list

```
for k in spam.keys(): 
	print(k)
```

* items()will return keys and values 

```
for i in spam.items():	print(i)
	
# Return values('color', 'red')('age', 42)
```

#### Checking Whether a Key or Value Exists in a Dictionary

* use the `in` or `not in` keyword along with either `keys()` or `values()` 

```
spam = {'name': 'Zophie', 'age': 7} 'name' in spam.keys()True
'Zophie' in spam.values()True'color' in spam.keys() False
'color' not in spam.keys() True'color' in spamFalse
```

#### The get() Method

* takes the key of the value to find and a fallback value to return if that key does not exist

`dictionary.get('key',fallbackValue)`
If key exists, will return key value, otherwise will return fallbackvalue

#### The setdefault() Method

* Alows you to set a key with a value
* If the key already exists, it returns the keys value.
* If it does not exist, returns sets the value to the key and returns it

`dictionary.setdefault(key,value)`

--
### Manipulating Strings

#### String Literals

* Begin and end with '

`'This is a string'`
* You can use double quotes, which is advised when punctuation/non letter characters are involed

`"This is also a string..."`

#### Escape characters

* use them in single quotes

#### Raw Strings

* These completely ignore any escape characters and prints \
* dont by putting a `r`just before the quote

Example

```
print(r'That is carol\'s cat')
#This returns
That is carol\'s cat.
```

#### Multiline Strings with Triple Quotes

* use `(''' string with multilines''')`

#### Multiline Comments

* Use `""" multiline comment"""`

#### Indexing and Slicing Strings

* This is done in the same way as lists ([indexStart:indexEnd])
* Will return a new list that has been sliced

#### In and Not in Operators with Strings

* Same as lists!

#### Useful String methods

* upper()
* lower()
* isupper()
* islower()

#### The isX String method

* These methods return booleans that have checked whether a list is a certain property

Examples:

* isAlpha()  (Returns true if list is only letters and is not blank)
* isalnum() (returns true if the string consists onyl of letters and numbers and is not blank)
* isdecimal() (returns true if list contains only numeric characters and is not blank)
* isspace (string only contains spaces, tabs and new lines and is not blank)
* istitle() (returns true if each word in the list starts with a uppercase and follows with lowercase characters)

#### Startswith(x) and endswith(x)

* Returns true if the string value(x) is at the start or end of the list 

#### join() and split()

* Join() adds two lists together
* split() takes a value and returns a list of values based on that split

Example

```
'My name is Simon'.split('m')#Return value['My na', 'e is Si', 'on']

```

#### Justifying Text with rjust(),ljust() and center()

* rJust(x) and ljust(y) just add characters to the front and end of  astring respectively, where x is the number of whitespaces/chracters
* center(numberOfChracters,characterToAdd) adds a number of the defined chracter to either side of the string, 

```
'Hello'.rjust(20, '*') '***************Hello''Hello'.ljust(20, '-') 'Hello---------------'Hello'.center(20)' Hello ' 'Hello'.center(20, '=') '=======Hello========'
```

#### Removing Whitesapce with strip(), rstrip() and lstrip()

* strip() removes white space charactes at the front and end of the string
* rstrip() removes whitepsace characters from the end of the string
* lstrip() removes whitespace characters from the front of the string

#### Copying and Pasting Strings with the pyperclip module

* This module has copy() and paste() functions that can send text to and receive text from your computers clipboard
* You have to import the `Pyperclip` module to do this.

```
import pyperclip
pyperclip.copy("hello world!")
pyperclip.paste()
```


--
## Automating Tasks

### Pattern Matching With Regular Expressions

#### Creating Regex Objects

* Need to import the `re` module
* to create a regex, you need to store in a variable and use `re.compile(regexpattern)`

#### Matching Regex Objects

* regex objects search method searches the string it is passed for any matches to the regex
* Returns None if nothing is found
* If pattern is found, returns a Match object.
* Match objects have group() mmethod that will return the actual matched text from the search string

Example

```
phoneNumRegex = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d') 
mo = phoneNumRegex.search('My number is 415-555-4242.') >>> print('Phone number found: ' + mo.group())
# OutputPhone number found: 415-555-4242
```
* Mo variable is a generaic name to use for match objects.
* .compile creates the regex object
*

#### Review of Regular Expression Matching

1. IMport the regex module `re`
2. Create a regex object with `re.compile` using a raw string
3. Pass the string you want to search into the regex objects `search()` method. This will return a match object or None
4. Call the Match objects `group` method to return a string of the actual matched text

--
### More Pattern matching With Regular expressions

#### Grouping with Parentheses

* By using regex groups (regex) (Regex)
* Can use the group method to return group values
* `.groups` returns all results

Example

```
>>> phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d-\d\d\d\d)') >>> mo = phoneNumRegex.search('My number is 415-555-4242.') >>> mo.group(1)'415'>>> mo.group(2) '555-4242'>>> mo.group(0) '415-555-4242' >>> mo.group() '415-555-4242'
>>> mo.groups()('415', '555-4242')>>> areaCode, mainNumber = mo.groups() >>> print(areaCode)415>>> print(mainNumber)555-4242
```

#### Matching Multiple Groups with the Pipe

* Pipes match one of many expressions (x|y)
* When both occurances are in the string, it will group the first and group the second, with each of these being match objects (by default will return the first occurance)

Example

```
>>> heroRegex = re.compile (r'Batman|Tina Fey') >>> mo1 = heroRegex.search('Batman and Tina Fey.') >>> mo1.group()'Batman'>>> mo2 = heroRegex.search('Tina Fey and Batman.') >>> mo2.group()'Tina Fey'

>>> batRegex = re.compile(r'Bat(man|mobile|copter|bat)') >>> mo = batRegex.search('Batmobile lost a wheel')>>> mo.group()'Batmobile'>>> mo.group(1) 'mobile'
```

#### Optional Matching With the Question Mark
* `?` flags the group that preceeds it as an optinal part of the pattern.

Example

```
>> batRegex = re.compile(r'Bat(wo)?man')>>> mo1 = batRegex.search('The Adventures of Batman') >>> mo1.group()'Batman'
```
This optinally matches "wo" (Matches 0 or more instances)

#### Matching Zero or More with Star

* The `*` means "match zero or one of the groups preceding this questionmark"

Example

```
>>> batRegex = re.compile(r'Bat(wo)*man')>>> mo1 = batRegex.search('The Adventures of Batman') >>> mo1.group()'Batman'>>> mo2 = batRegex.search('The Adventures of Batwoman') >>> mo2.group()'Batwoman'>>> mo3 = batRegex.search('The Adventures of Batwowowowoman') >>> mo3.group()'Batwowowowoman'
```

#### Matching One or More with +

* `+` means "match one or more"
* Unlike star, it requires a group prceeding it at least once.

Example

```
>>> batRegex = re.compile(r'Bat(wo)+man')>>> mo1 = batRegex.search('The Adventures of Batwoman') >>> mo1.group()'Batwoman'>>> mo2 = batRegex.search('The Adventures of Batwowowowoman') >>> mo2.group()'Batwowowowoman'
>>> mo3 = batRegex.search('The Adventures of Batman') >>> mo3 == NoneTrue
```

#### Matching Specific Repetitions with Curly Brackets

* If you want to repeat a group a certain amount of ot imes, follow the group with `{x}`, where x is the number of times.
* You can give it a range as well `{x,y}`

Example

```
>>> haRegex = re.compile(r'(Ha){3}') 
>>> mo1 = haRegex.search('HaHaHa') 
>>> mo1.group()'HaHaHa'

>>> mo2 = haRegex.search('Ha') 
>>> mo2 == NoneTrue
```

#### Greedy and Nongreedy Matching

* Pythons regular expressions are greedy by default. The match the longest string possible
* The curly brackets make it non greedy, meaning that it matches the smallest string possible

Example

```
>>> greedyHaRegex = re.compile(r'(Ha){3,5}') >>> mo1 = greedyHaRegex.search('HaHaHaHaHa') >>> mo1.group()'HaHaHaHaHa'>>> nongreedyHaRegex = re.compile(r'(Ha){3,5}?') >>> mo2 = nongreedyHaRegex.search('HaHaHaHaHa') >>> mo2.group()'HaHaHa'
```

#### The findall() method

* Regex objects hav ea findall() method
* Where search() will return a mathc object of the first matched text in the string, findall returns the strings of every match in a searched string
* When there are no groups in a regex (where things are not in brackets), find al returns  alist of string of mathces
* When there are groups, it returns a list of tuple of strings [('x'),)('y)]

#### Character Classes

* These are short hand regular expressions
* Types of character classes:
	* \d (Any number from 0 to 9)
	* \D (Any character that is not numberic from 0 to 9)
	* \w (Any letter, number or underscore)
	* \W (Any character that is not a letter, numbr or underscore)
	* \s (Any space, tab or new line character)
	* \S (Any character that is not a space, tab or newline

#### Making Your Own Character Classes

* Done by using []
* Example [aeiouAEIOU] will match any vowel

Example

```
>>> vowelRegex = re.compile(r'[aeiouAEIOU]')>>> vowelRegex.findall('RoboCop eats baby food. BABY FOOD.') ['o', 'o', 'o', 'e', 'a', 'a', 'o', 'o', 'A', 'O', 'O']
```

#### The Caret and Dollar Sign Characters

* Can use `^` at the start of a regex
* This indicates that a match must occur at the beginning of the searched text
* `$` can be placed at the end, to indicate the string must end with this pattern

#### The Wildcard Character

* `.` matches any character (Aka a wildcard)
* Will only match one character, not strings/words

Example

```>>> atRegex = re.compile(r'.at')>>> atRegex.findall('The cat in the hat sat on the flat mat.') 
>>> ['cat', 'hat', 'sat', 'lat', 'mat']
```

#### Matching Everything with Dot-Star

* `.*` matches everything and anything
* This is greedy - It will match as much as possible
* To make it non greedy, use `(.*?)`

Example

```
>>> nameRegex = re.compile(r'First Name: (.*) Last Name: (.*)') >>> mo = nameRegex.search('First Name: Al Last Name: Sweigart') >>> mo.group(1)'Al'>>> mo.group(2) 'Sweigart'
```

#### Matching Newlines with Dot Character

* `.` matches everything APART from new line
* you can make it match new lines by passing `re.DOTALL)` to the `re.compile()` method

Example

```
>>> noNewlineRegex = re.compile('.*')>>> noNewlineRegex.search('Serve the public trust.\nProtect the innocent. \nUphold the law.').group()'Serve the public trust.'
>>> newlineRegex = re.compile('.*', re.DOTALL)>>> newlineRegex.search('Serve the public trust.\nProtect the innocent. \nUphold the law.').group()'Serve the public trust.\nProtect the innocent.\nUphold the law.'
```

#### Sibstituting Strings with the sub() Method

* Regular expressions can also substitue new text in the place of a pattern
* `sub(StringToReplace, ValueToPutInReplacedStringsPosition)`

```
>>> namesRegex = re.compile(r'Agent \w+')>>> namesRegex.sub('CENSORED', 'Agent Alice gave the secret documents to Agent Bob.') 
'CENSORED gave the secret documents to CENSORED.'
```

#### Combining re.IGNORECASE, re.DOTALL, and re.VERBOSE

* By default re.compile() can only take one of the above.
* To use multiple, use |

```
>>> someRegexValue = re.compile('foo', re.IGNORECASE | re.DOTALL | re.VERBOSE)
```
--
### Reading and Writing Files

#### Files and File Paths

* Files have two key properties:
	* A filename
	* A path (Location on the computer)

#### Backslash on Windows and Forward Slash on OSX and Linux

* Windows pathes use \ whereas linux and mac paths use /
* To deal with this, you can use `os.path.join` from the os module. 
* This will create a string  given a series of folders that represent the path

```
>>> import os>>> os.path.join('usr', 'bin', 'spam') 
'usr\\bin\\spam'
```

* You can also create a list of files, and python will get the file paths for you.

```
>>> myFiles = ['accounts.txt', 'details.csv', 'invite.docx'] 
>>> for filename in myFiles:  print(os.path.join('C:\\Users\\asweigart', filename))
#Printed results:C:\Users\asweigart\accounts.txtC:\Users\asweigart\details.csvC:\Users\asweigart\invite.docx
```

#### The Current Working Directory

* Every program has a current working directory or cwd
* Filenames or paths that do not begin with a root folder are assumed to be under the current working directory
* Can get the current working directory as a string value by using `os.getcwd()`
* Can change the current working directory using `os.chdir()`
	* If this directory does not exist, a error is thrown rather than creating that directory


Example

```
>>> import os>>> os.getcwd()'C:\\Python34'>>> os.chdir('C:\\Windows\\System32') 
>>> os.getcwd() 
'C:\\Windows\\System32'
```

#### Absolute vs. Relative Paths

* Abolsute paths always begin with the root folder
* Relative paths are relative to the current working directory
* (.) represents this directory
* (..) represents the parent directory

#### Creating New Folders with os.makedirs() 

* This can be done with `os.makedirs(Path)`
* Will create all necessary folders if the path does not exist

#### Handling Absolute and Relative Paths

* `os.path.abspath(path)` will return a string of the absoolute path
* `os.path.isabs(path)` will return True if the argument is an absolute path and False if it is a relative path
* `os.path.relpath(path)` will return the relative path from the start of the path. If the start of the path is not provided, it will return the current working directory 

Examples

```
>>> os.path.abspath('.')'C:\\Python34'>>> os.path.abspath('.\\Scripts') 
'C:\\Python34\\Scripts'>>> os.path.isabs('.')False>>> os.path.isabs(os.path.abspath('.'))
True
```

* `os.path.basename(path)` will return everything after the last \
* `os.path.dirname(path)` will return everything before the last \

Example

```
>>> path = 'C:\\Windows\\System32\\calc.exe' 
>>> os.path.basename(path)'calc.exe'>>> os.path.dirname(path) 
'C:\\Windows\\System32'
```

* If you need both the paths dir name and base name, can use `os.path.split(filePath)` that will return a tuple of the dirname and base name

Example

```
>>> calcFilePath = 'C:\\Windows\\System32\\calc.exe' 
>>> os.path.split(calcFilePath) 
('C:\\Windows\\System32', 'calc.exe')
```

* You can use `.split(os.path.sep)` to get a list, which the first element is the start of the path, and the last element is the basename

Example

```
 >>> calcFilePath.split(os.path.sep) 
 ['C:', 'Windows', 'System32', 'calc.exe']
```

#### Finding File Size and Folder Contents

* `os.path` module provides functions for finding the size of a file in bytes, and the files and folders inside a given folder
* `os.path.getsize(path)` will return the size in bytes of the file in the path argument
* `os.listdir(path)` will return a list of filename strings for each file in the `path` arugment

Example

```
>>> os.path.getsize('C:\\Windows\\System32\\calc.exe')776192>>> os.listdir('C:\\Windows\\System32')['0409', '12520437.cpx', '12520850.cpx', '5U877.ax', 'aaclient.dll', --snip--                 'xwtpdui.dll', 'xwtpw32.dll', 'zh-CN', 'zh-HK', 'zh-TW', 'zipfldr.dll']

```

Example 2, Ugetting the total size of all the files in the directory using `os.path.getsize()` and `os.listdir()`

```
>>> totalSize = 0>>> for filename in os.listdir('C:\\Windows\\System32'):      totalSize = totalSize + os.path.getsize(os.path.join('C:\\Windows\\System32', filename))>>> print(totalSize) 
1117846456      
```

#### Checking Path Validity

* `os.path.exists(path)` will return True if the file or filder exists and false is it does not
* `os.path.isfile(path)` will return True if the path arugment exists and is a file otherwise false
* `os.path.isdir(path)` will return True if the path argument exists and is a folder, otherwise false


Example

```
>>> os.path.exists('C:\\Windows')True>>> os.path.exists('C:\\some_made_up_folder')False>>> os.path.isdir('C:\\Windows\\System32')True>>> os.path.isfile('C:\\Windows\\System32')False>>> os.path.isdir('C:\\Windows\\System32\\calc.exe') 
False>>> os.path.isfile('C:\\Windows\\System32\\calc.exe') 
True
```

#### The File Reading/Writing Process

The steps for reading or writing files in Python are:

1. Call open() to get a File Object
2. Call read() or write() on the File Object
3. Close the file using close() on the File Object

#### Opening Files with the Open() Function

* Remember that you cant write to a file which you have opened in read mode
* Write mode overwrites the current file and starts from scratch
* To open the file, use open(filename,howToTreatTheFile)
* How to treat the file can be one of the following:
	* 'w' = write mode (Overwrites the file)
	* 'a' = append mode (Adds text to the end of the file)
* If the file noes not exist, it will create it for you

Example
```
>>> baconFile = open('bacon.txt', 'w') 
>>> baconFile.write('Hello world!\n') 13>>> baconFile.close()>>> baconFile = open('bacon.txt', 'a')>>> baconFile.write('Bacon is not a vegetable.') 25>>> baconFile.close()>>> baconFile = open('bacon.txt')>>> content = baconFile.read()>>> baconFile.close()>>> print(content)Hello world!Bacon is not a vegetable.
```

#### Saving Variables with the shelve Module

* Can save variables in your program to binary shelf files using the `shelve` module
* Shelve files are treated as dictionaries (key:value pairs)

Example of saving to a shelve file

```
>>> import shelve>>> shelfFile = shelve.open('mydata') >>> cats = ['Zophie', 'Pooka', 'Simon'] >>> shelfFile['cats'] = cats>>> shelfFile.close()
```

Steps:

1. Import shelve module
2. Call `shelve.open(fileName)` and store in a variable
3. store the variable in the shelve file using `shelveFile[variable] = variableAlreadyDefined`
4. close the shelve file 

Example of reading a shelve file

```
>>> shelfFile = shelve.open('mydata') >>> type(shelfFile)<class 'shelve.DbfilenameShelf'>>>> shelfFile['cats']['Zophie', 'Pooka', 'Simon'] >>> shelfFile.close()
```

Steps:

1. Open the shelve file
2. Get the variable you want using `shelfFile['variableName']


* As mentioned above, these are treated as dictionaryies.
* They have keys() and values() methods
* These return list-like values, so you should pass them to the list() function

Example


```
>>> shelfFile = shelve.open('mydata') >>> list(shelfFile.keys())['cats']>>> list(shelfFile.values()) [['Zophie', 'Pooka', 'Simon']]>>> shelfFile.close()

```

#### Saving Variables with the print.pformat() Function

* pprint.pformat() can be used to make printing easier to read
* These return strings which can written to .py files.

```
>>> import pprint>>> cats = [{'name': 'Zophie', 'desc': 'chubby'}, {'name': 'Pooka', 'desc': 'fluffy'}] >>> pprint.pformat(cats)"[{'desc': 'chubby', 'name': 'Zophie'}, {'desc': 'fluffy', 'name': 'Pooka'}]">>> fileObj = open('myCats.py', 'w')>>> fileObj.write('cats = ' + pprint.pformat(cats) + '\n')83>>> fileObj.close()

```
--

### Organizing Files

#### The shutil Module

* This module gives you functions to copy, move, rename and delete files.
* Remember to import the module!

#### Copying Files and Folders

* To copy a file, use `shutil.copy(source, destination)` Where source and destination are strings
* if you decided to make desination a filename, the file will be renamed
* This function will return a string of the path of copied file

Example

```
>>> import shutil, os>>> os.chdir('C:\\')>>> shutil.copy('C:\\spam.txt', 'C:\\delicious')'C:\\delicious\\spam.txt'>>> shutil.copy('eggs.txt', 'C:\\delicious\\eggs2.txt')'C:\\delicious\\eggs2.txt'
```

* you can use `shutil.copytree(source, newDiretory)` to copy a folder with all its cotents into a new directory (keeps the source directory as well

Example

```
>>> import shutil, os>>> os.chdir('C:\\')>>> shutil.copytree('C:\\bacon', 'C:\\bacon_backup') 
'C:\\bacon_backup'
```

#### Moving and Renaming Files and Folders

* `shutil.move(source, destination)` will move a file or folder to a new location
* Source and destinations should be strings of the paths you want to use
* If destination ppoints to a folder, source gets moved into desination and keeps the file name
* * If there is a file with the same name in the directory, it is over written
* Folders that make the destination must already exist, or you will get an error from Python

Example

```>>> import shutil>>> shutil.move('C:\\bacon.txt', 'C:\\eggs') 
'C:\\eggs\\bacon.txt'

```

* Desination path can specify a file name. This will rename the file you want to move

Example

```
>>> shutil.move('C:\\bacon.txt', 'C:\\eggs\\new_bacon.txt') 'C:\\eggs\\new_bacon.txt'

```

* If there was no eggs folder in the above examples, move() would rename bacon.txt to eggs

Example

```
>>> shutil.move('C:\\bacon.txt', 'C:\\eggs') 
'C:\\eggs'
```

#### Permanently Deleting Files and Folders

* `os.unlink(path)` will delete the file at path
* `os.rmdir(path)` will delete the folder at path. This folder must be empty
* `shutil.rmtree(path)` will remove the folder at path with its contents

#### Safe Deletes with the send2trash Module

* Using this module will send files and folders to the trash can, rather than deleting them perminantly
* Can be install useding `pip install send2trash` from the terminal window

Example

```
>>> import send2trash>>> baconFile = open('bacon.txt', 'a') # creates the file >>> baconFile.write('Bacon is not a vegetable.')25>>> baconFile.close()>>> send2trash.send2trash('bacon.txt')
```

* Its good pratice to use `send2trash.send2trash()` to delete files and folders


#### Walking a Directory Tree

* you can use `os.walk()` and a loop to get information of all subfolders in a directory

Example

```
import osfor folderName, subfolders, filenames in os.walk('C:\\delicious'):      print('The current folder is ' + folderName)             for subfolder in subfolders:                   print('SUBFOLDER OF ' + folderName + ': ' + subfolder)
              for filename in filenames:                   print('FILE INSIDE ' + folderName + ': '+ filename)				  print('')

```

The avoce function will return the following values on each iteration:

1. A string of the current folders name
2. A list of strings of the folders in the current folder
3. A list of strings of the files in the current folder


#### Compressing Files with the Zipfile Module

##### Reading Zip Files

* Have to create a ZipFile Object(Captial Z and F)
* To create a zipfile object, call `zipfile.ZipFile(StringOfZipFilesName)`

Example

```
>>> import zipfile, os>>> os.chdir('C:\\') # move to the folder with example.zip >>> exampleZip = zipfile.ZipFile('example.zip')>>> exampleZip.namelist()['spam.txt', 'cats/', 'cats/catnames.txt', 'cats/zophie.jpg'] >>> spamInfo = exampleZip.getinfo('spam.txt')>>> spamInfo.file_size13908>>> spamInfo.compress_size3828>>> 'Compressed file is %sx smaller!' % (round(spamInfo.file_size / spamInfo .compress_size, 2))'Compressed file is 3.63x smaller!'>>> exampleZip.close()

```

##### Extracting from ZIP Files

* `extractall()`  will extract everything inside a ZIP file into the current working directory

Example

```
>>> import zipfile, os>>> os.chdir('C:\\') # move to the folder with example.zip >>> exampleZip = zipfile.ZipFile('example.zip')>>> exampleZip.extractall() >>> exampleZip.close()
```

* `extract(fileInsideZip)` can be used to extract a single file from the zip.

Example

```
>>> exampleZip.extract('spam.txt')'C:\\spam.txt'>>> exampleZip.extract('spam.txt', 'C:\\some\\new\\folders') 
'C:\\some\\new\\folders\\spam.txt'>>> exampleZip.close()
```

##### Creating and Adding to ZIP Files

* To create your own ZIP, must open a ZipFile object in write mode (By passing 'w') as the second argument
* To add t the zip, you need to use `write(fileToAdd, CompressionType)`
* You must close the zip

Example

```>>> import zipfile>>> newZip = zipfile.ZipFile('new.zip', 'w')>>> newZip.write('spam.txt', compress_type=zipfile.ZIP_DEFLATED) >>> newZip.close()
```

--
### Debugging

#### Raising Exceptions

* Exceptions are thrown when python tries to execute invalid code
* Exceptions are created with `raise` statements
* `raise` statements consist of:
	* The `raise` keyword
	* A call to the `Exception()` function
	* A string with a helpful error message which is passed to the `Exception()` function

Example

```
>>> raise Exception('This is the error message.')
```

* If you do not have try and except statements around an exception, the program will crash and display the erorr message
* Try statements are put around code that can produce exceptions.
* except statements catch exceptions and allow you to deal with them.

Example

```
try:        boxPrint(sym, w, h)except Exception as err:        print('An exception happened: ' + str(err))
```

#### Getting Traceback

* Trackbacks are details on what caused the exception.
* You can put these in a text file for easier reading
* Need to import traceback

Example


```
>>> import traceback 
>>> try:         raise Exception('This is the error message.')except:         errorFile = open('errorInfo.txt', 'w')         errorFile.write(traceback.format_exc())         errorFile.close()         print('The traceback info was written to errorInfo.txt.')

```

#### Assertions

* Used to make sure you code is working correctly
* If the assert fails, it raises an `assertionError` exception
* Asserts consist of:
	* The assert keyword
	* A condition (That must evaluate to true or false)
	* A comma
	* A string to display when the condition is false

Example

```
>>> podBayDoorStatus = 'open'>>> assert podBayDoorStatus == 'open', 'The pod bay doors need to be "open".' 
>>> podBayDoorStatus = 'I\'m sorry, Dave. I\'m afraid I can't do that.''>>> assert podBayDoorStatus == 'open', 'The pod bay doors need to be "open".' 

 Traceback (most recent call last):       File "<pyshell#10>", line 1, in <module>          assert podBayDoorStatus == 'open', 'The pod bay doors need to be "open".'      AssertionError: The pod bay doors need to be "open"
```

* you can disable assertions using the flag `-o`

#### Logging

--
### WebScraping

#### Opening Web pages

* webbrowsers modules open() function can launch webpages based on a url

Example

```
>>> import webbrowser>>> webbrowser.open('http://inventwithpython.com/')
```

#### Downloading Files from the Web With the Requests Module

* requests module lets you download files.
* This does not come with python, so you'll have to install it by entering the following in terminal: `pip install requests` (see end of guide on how to install third party modules)


#### Downloading a Web Page with the requests.get() Function

* tajkes a String that represents the URL to download
* This returns a Responce object.
* Response objects contain the responce from the web server you want to get thepage from

Example

```
>>> import requests>>> res = requests.get('http://www.gutenberg.org/cache/epub/1112/pg1112.txt')>>> type(res)<class 'requests.models.Response'> 
>>> res.status_code == requests.codes.okTrue>>> len(res.text)178981>>> print(res.text[:250])The Project Gutenberg EBook of Romeo and Juliet, by William Shakespeare             This eBook is for the use of anyone anywhere at no cost and with             almost no restrictions whatsoever.  You may copy it, give it away or             re-use it under the terms of the Proje
```

* Can tell if a request for the webpage is successful by checking the `status_code_` attribute of the Response object

#### Checking for Errors

* call `raise_for_status()` on the Responce object
* Will raise an exception if there was an error downloading the file
* Its good practice to use this before downloading something to ensure nothing bad happens.
* Always `raise_for_status()` after `requests.get()`


Example

```
import requests        res = requests.get('http://inventwithpython.com/page_that_does_not_exist')         try:               res.raise_for_status()         except Exception as exc: 					print('There was a problem: %s' % (exc))
```

#### Saving Downloaded Files to the Hard Drive

* once you have used .get to get the page, you can use the standard open() and write() 
* You **MUST** open the file in write binary mode ('wb') as the second argument to open
* You then use a for loop with the Responce objects `iter_content()` method to get everything on the page

Example

```
>>> import requests>>> res = requests.get('http://www.gutenberg.org/cache/epub/1112/pg1112.txt') >>> res.raise_for_status()>>> playFile = open('RomeoAndJuliet.txt', 'wb')>>> for chunk in res.iter_content(100000):                     playFile.write(chunk)10000078981>>> playFile.close()

```

Summarized process:

1. Use `requests.get()` to download the file
2. `open(filename,'wb')`
3. Loop over the Responce object using `iter_content()`
4. `write()` on each iteration
5. `close()` file

#### Parsing HTML with the BeatifulSoup Module

* Known as BS4. 
* Have to install by: `pip install beautifulsoup4`

#### Creating a BeautifulSoup Object from HTML

* `bs4.BeautifulSoup() must be given a string containing HTML to be parsed.
* Returns a beautifulSoup object
* Should use `requests.get(URl)` to get the webpage object, the give it to BeatifulSoup in text format
Example

```
>>> import requests, bs4>>> res = requests.get('http://nostarch.com') >>> res.raise_for_status()>>> noStarchSoup = bs4.BeautifulSoup(res.text) >>> type(noStarchSoup)<class 'bs4.BeautifulSoup'>
```

* Can load a HTML file from your hard drive by passing a File Object to bs4.BeautifulSoup()
* Make sure the HTML file is in your working directory!

Example

```
>>> exampleFile = open('example.html')>>> exampleSoup = bs4.BeautifulSoup(exampleFile) >>> type(exampleSoup)<class 'bs4.BeautifulSoup'>
```

#### Finding an Element with the select() Method

* Select(cssSelector) finds a element based on the css selector you pass to it.
* The following are examples of CSS Selectors:
	* `soup.select('div')` = All elements named `<div>`
	* `soup.select('#author')` = The element with an id attribute of author
	* `soup.select('.notice')` = All elements that use a CSS class attribute named notice
	* `soup.select('div span')` =All elements named `<span>` that are within an element named `<div>`
	* `soup.select('div > span')` = All elements named `<span>` that are directly within an element named `<div>`, with no other element in between
	* `soup.select('input[name]')` = All elements named `<input>` that have a name attribute with any value
	* `soup.select('input[type="button"]')` = All elements named `<input> `that have an attribute named type with value button
* `Select` will return a list of Tag objects, which is how Beautiful Soup represents an HTML Element.
* Lists will contain one tag object per match in the HTML
* Tag values can be passed to `str()` to show the HTML tag they represent
* Tags also have `attrs`, this shows all the HTML attributes of the tag as a dictionary

Example

```
>>> import bs4>>> exampleFile = open('example.html')>>> exampleSoup = bs4.BeautifulSoup(exampleFile.read()) 
>>> elems = exampleSoup.select('#author')>>> type(elems)<class 'list'>>>> len(elems)1>>> type(elems[0])<class 'bs4.element.Tag'>>>> elems[0].getText()'Al Sweigart'>>> str(elems[0])'<span id="author">Al Sweigart</span>'>>> elems[0].attrs{'id': 'author'}
```

#### Getting Data from an Element's Attributes

* use the `.get(attribute)` method on element.
* Will return the text value of the object.

Example

```
>>> import bs4>>> soup = bs4.BeautifulSoup(open('example.html')) >>> spanElem = soup.select('span')[0]>>> str(spanElem)'<span id="author">Al Sweigart</span>'>>> spanElem.get('id')'author'>>> spanElem.get('some_nonexistent_addr') == None True>>> spanElem.attrs{'id': 'author'}
```

#### Controlling the Browser with the Selenium Module


* Need to use `from selenium import webdriver`
* to start the browser:

```
>>> from selenium import webdriver>>> browser = webdriver.Firefox()>>> type(browser)<class 'selenium.webdriver.firefox.webdriver.WebDriver'>
>>> browser.get('http://inventwithpython.com')
```

#### Finding Elements on the Page

* `find_element_*` returns the first element on the page that meets your criteria
* `find_elements_*` returns all elements that meet your criteria on a page.
* Find element(s) Permutations:
	* `browser.find_element_by_class_name(name)`
	* `browser.find_elements_by_class_name(name)`
	* `browser.find_element_by_css_selector(selector)` 
	* `browser.find_elements_by_css_selector(selector)`
	* `browser.find_element_by_id(id) `
	* `browser.find_elements_by_id(id)`
	* `browser.find_element_by_link_text(text)`
	* `browser.find_elements_by_link_text(text)`
	* `browser.find_element_by_partial_link_text(text)`
	* `browser.find_elements_by_partial_link_text(text)`
	* `browser.find_element_by_name(name)`
	* `browser.find_elements_by_name(name)`
	* `browser.find_element_by_tag_name(name)`
	* `browser.find_elements_by_tag_name(name)`
* The above method sare case sensitive

Example

```

from selenium import webdriverbrowser = webdriver.Firefox()browser.get('http://inventwithpython.com')
try:    elem = browser.find_element_by_class_name('bookcover')    print('Found <%s> element with that class name!' % (elem.tag_name))except:    print('Was not able to find an element with that name.')
    
```   

* You can get details of the element by using the following methods on a found element:
	* `tag_name`
	* `get_attribute(name)`
	* `text`
	* `clear()`
	* `is_displayed()`
	* `is_enabled()`
	* `is_selected()`
	* `location`   (returns dictionary with x y position)
 
#### Clicking the page

* Use `click` on the element object

```
>>> from selenium import webdriver>>> browser = webdriver.Firefox()>>> browser.get('http://inventwithpython.com')>>> linkElem = browser.find_element_by_link_text('Read It Online') >>> type(linkElem)<class 'selenium.webdriver.remote.webelement.WebElement'>>>> linkElem.click() # follows the "Read It Online" link
```

#### Filling Out and Submitting Forms

* Need to find the text area or input and then use `send_keys()`

Example

```
>>> from selenium import webdriver>>> browser = webdriver.Firefox()>>> browser.get('http://gmail.com')>>> emailElem = browser.find_element_by_id('Email')>>> emailElem.send_keys('not_my_real_email@gmail.com') >>> passwordElem = browser.find_element_by_id('Passwd')
>>> passwordElem.send_keys('12345') 
>>> passwordElem.submit()

```

* To send special keys, the selenium.webdriver.common.keys module.
(Best to do it as `from selenium.webdriver .common.keys import Keys`)

Example (not listing all keys here)

```
>>> from selenium import webdriver>>> from selenium.webdriver.common.keys import Keys>>> browser = webdriver.Firefox()>>> browser.get('http://nostarch.com')>>> htmlElem = browser.find_element_by_tag_name('html') 
>>> htmlElem.send_keys(Keys.END) # scrolls to bottom >>> htmlElem.send_keys(Keys.HOME) # scrolls to top

```

#### Clicking browser buttons

* Selenium provides the following:
	* browser.back()
	* browser.forward()
	* browser.refresh()
	* browser.quit()

--
### Working With Excel Spreadsheets

**CONTINUE**
--
### Working With PDF and Word Documents 

* Need to use the PyPDF2 module. 
* Can be installed using pip
* PDFs are very hard to parase, so PyPDF2 might make some mistakes.


#### Extracting Text from PDFs

* PyPDF2 cannot extract images, charts or other media from PDFs.
* However it can extract text and return it as a string
* You do this by specifying the page with `pdfReader.getPage(x)` then using `.extractText()`

Example

```
>>> import PyPDF2>>> pdfFileObj = open('meetingminutes.pdf', 'rb') >>> pdfReader = PyPDF2.PdfFileReader(pdfFileObj)>>> pdfReader.numPages 19>>> pageObj = pdfReader.getPage(0) >>> pageObj.extractText()
```

#### Decrypting PDFs

* Some PDFs come encrypted.
* You can specify the password that is needed in your python code by using `.decrypt('rosebud')`
* If you close the python program then try and open it in a new python program, you have to decrypt it again

Example

```
>>> import PyPDF2>>> pdfReader = PyPDF2.PdfFileReader(open('encrypted.pdf', 'rb'))
>>> pdfReader.decrypt('rosebud') 
1>>> pageObj = pdfReader.getPage(0)
```

#### Creating PDFs

* You can use PdfFileWriter objects to create new PDF files.
* Unfortinately PyPDF2 can only copy pages, rotating pages, overlaying pages and encrypting files, not writing directly to a new file.
* You cannot directly edit a PDF. You have to create a new PDF then copy the content over.

Steps:

1. Open one or more PDfs into PdfFileReader objects
2. Create a new PdfFileWriter object
3. Copy pages from the PdfFileReader object into the PdfFileWriter object
4. Use the PdfFileWriter object to write the output PDF
5. Then call PdfFilesWriter's `write()`

#### Copying Pages.

Example

```
>>> import PyPDF2>>> pdf1File = open('meetingminutes.pdf', 'rb') 
>>> pdf2File = open('meetingminutes2.pdf', 'rb')>>> pdf1Reader = PyPDF2.PdfFileReader(pdf1File) 
>>> pdf2Reader = PyPDF2.PdfFileReader(pdf2File) 
>>> pdfWriter = PyPDF2.PdfFileWriter()>>> for pageNum in range(pdf1Reader.numPages):pageObj = pdf1Reader.getPage(pageNum)pdfWriter.addPage(pageObj)>>> for pageNum in range(pdf2Reader.numPages):pageObj = pdf2Reader.getPage(pageNum)pdfWriter.addPage(pageObj)>>> pdfOutputFile = open('combinedminutes.pdf', 'wb') >>> pdfWriter.write(pdfOutputFile)>>> pdfOutputFile.close()>>> pdf1File.close()>>> pdf2File.close()
```

#### Rotating Pages

* use `rotateClockwise(degrees)` or `rotateCounterClockwise(degrees)`
* Degrees can be one of the following:
	* 90
	* 180
	* 270

Example

```
>>> import PyPDF2>>> minutesFile = open('meetingminutes.pdf', 'rb') 
>>> pdfReader = PyPDF2.PdfFileReader(minutesFile)>>> page = pdfReader.getPage(0) 
>>> page.rotateClockwise(90){'/Contents': [IndirectObject(961, 0), IndirectObject(962, 0), 
--snip--}>>> pdfWriter = PyPDF2.PdfFileWriter()>>> pdfWriter.addPage(page)>>> resultPdfFile = open('rotatedPage.pdf', 'wb')>>> pdfWriter.write(resultPdfFile) >>> resultPdfFile.close()>>> minutesFile.close()

```

#### Encrypting PDFs

* Use `.encrypt(password)`

Example

```
>>> import PyPDF2>>> pdfFile = open('meetingminutes.pdf', 'rb') 
>>> pdfReader = PyPDF2.PdfFileReader(pdfFile) 
>>> pdfWriter = PyPDF2.PdfFileWriter()>>> for pageNum in range(pdfReader.numPages):           pdfWriter.addPage(pdfReader.getPage(pageNum))>>> pdfWriter.encrypt('swordfish')>>> resultPdf = open('encryptedminutes.pdf', 'wb') >>> pdfWriter.write(resultPdf)>>> resultPdf.close()
```


#### Reading Word Documents

CONTNIUE

--
### Working with CSV Files and JSON Data

#### The CSV Module

* Each line in a CSV file represesnts a row in the spreat sheet
* Commars are used to seperate the cells in a row

Example CSV

```
4/5/2015 13:34,Apples,734/5/2015 3:41,Cherries,854/6/2015 12:46,Pears,144/8/2015 8:59,Oranges,524/10/2015 2:07,Apples,1524/10/2015 18:10,Bananas,234/10/2015 2:40,Strawberries,98
```

#### Reader Objects

* Reader objects are used to read CSV files from the csv module
* These objects allow you to iterate over the lines in a csv file
* You need to open the csv file then use `.reader()` on it
* Once that is done you can place the CSV file in a list, with each index representing a line from the CSV file


Example

```
>>> import csv>>> exampleFile = open('example.csv') 
>>> exampleReader = csv.reader(exampleFile) 
>>> exampleData = list(exampleReader)
>>> exampleData   [['4/5/2015 13:34', 'Apples', '73'], ['4/5/2015 3:41', 'Cherries', '85'],   ['4/6/2015 12:46', 'Pears', '14'], ['4/8/2015 8:59', 'Oranges', '52'],   ['4/10/2015 2:07', 'Apples', '152'], ['4/10/2015 18:10', 'Bananas', '23'],   ['4/10/2015 2:40', 'Strawberries', '98']]

# Format is [x][y]
>>> exampleData[0][0] 
'4/5/2015 13:34'>>> exampleData[0][1] 
'Apples'>>> exampleData[0][2] 
'73'>>> exampleData[1][1] 
'Cherries'>>> exampleData[6][1] 
'Strawberries'
```


#### Reading Data from Reader Objects in a for loop

* For large CSV files, you need to use the Reader object in a for loop.
* Doing this will avoid loading the entire file into memory at once

Example

```
>>> import csv>>> exampleFile = open('example.csv')>>> exampleReader = csv.reader(exampleFile) 
>>> for row in exampleReader:           print('Row #' + str(exampleReader.line_num) + ' ' + str(row))
              Row #1 ['4/5/2015 13:34', 'Apples', '73']   Row #2 ['4/5/2015 3:41', 'Cherries', '85']   Row #3 ['4/6/2015 12:46', 'Pears', '14']   Row #4 ['4/8/2015 8:59', 'Oranges', '52']   Row #5 ['4/10/2015 2:07', 'Apples', '152']   Row #6 ['4/10/2015 18:10', 'Bananas', '23']   Row #7 ['4/10/2015 2:40', 'Strawberries', '98']
```

#### Writer Objects

* Writer objects allow you to write data to a CSV file
* You create Writer objects using `csv.writer()`
* To write a row, use `writerow(list)`
* Remember to close the object when you are done!!

Example

```
>>> import csv>>> outputFile = open('output.csv', 'w', newline='') 
>>> outputWriter = csv.writer(outputFile)>>> outputWriter.writerow(['spam', 'eggs', 'bacon', 'ham'])21>>> outputWriter.writerow(['Hello, world!', 'eggs', 'bacon', 'ham']) 32>>> outputWriter.writerow([1, 2, 3.141592, 4])16>>> outputFile.close()
```

#### The Delimiter and Lineterminator Keyword Arguments

* To can use the delimter keyword to state how the CSV entries should be seperated
* You can use the lineterminator tab to state what the program should do after the end of line is reached (By default, this will give you a blank line in between rows)

Example

```
>>> import csv>>> csvFile = open('example.tsv', 'w', newline='')>>> csvWriter = csv.writer(csvFile, delimiter='\t', lineterminator='\n\n')>>> csvWriter.writerow(['apples', 'oranges', 'grapes']) 24>>> csvWriter.writerow(['eggs', 'bacon', 'ham'])17>>> csvWriter.writerow(['spam', 'spam', 'spam', 'spam', 'spam', 'spam']) 32>>> csvFile.close()
```

#### JSON and APIs

* JSON is a way to format ata as a human readable string
* JSON is the native way that javascript stores its data structures

Example JSON file:

```
{"name": "Zophie", "isCat": true, "miceCaught": 0, "napsTaken": 37.5, "felineIQ": null}
```
#### The JSON Module

* Handles all the details of translating between a string with JSON data and Python values.
* JSON can store the following data types:
	* Strings
	* Integers
	* Floats
	* Booleans
	* Lists
	* Dictionaries
	* NonType
* Cannot represent python specific types (eg, Regex, Writer so on...)

#### Reading JSON with the loads() Function

* `json.loads(JSONString)` translates JSON data into a python Dictionary (Note, ordering is not kept, this may be different to the order it was in the JSON file!)
* The JSON String MUST be in double quotes!

Example

```
>>> stringOfJsonData = '{"name": "Zophie", "isCat": true, "miceCaught": 0, "felineIQ": null}'>>> import json>>> jsonDataAsPythonValue = json.loads(stringOfJsonData)>>> jsonDataAsPythonValue{'isCat': True, 'miceCaught': 0, 'name': 'Zophie', 'felineIQ': None}
```

#### Writing JSON with the dumps() Function

* `json.dumps(pythonValue)` takes a python value and turns it into a JSON-formatted string.

Example

```
>>> pythonValue = {'isCat': True, 'miceCaught': 0, 'name': 'Zophie', 'felineIQ': None}>>> import json>>> stringOfJsonData = json.dumps(pythonValue)>>> stringOfJsonData'{"isCat": true, "felineIQ": null, "miceCaught": 0, "name": "Zophie" }'
```
--
### Keeping Time, Scheduling Tasks, and Launching Programs

* The time module allows you to get the current time from your system clock.

#### time.time() Function

* `time.time()` returns a floating point number that represents the current time since the "Unix epoch"

Example

```
>>> import time 
>>> time.time() 
1425063955.068649
```
Example of time it takes to run a method

```
import time udef calcProd():       # Calculate the product of the first 100,000 numbers.       product = 1       for i in range(1, 100000):           product = product * i       return productstartTime = time.time() prod = calcProd()endTime = time.time()print('The result is %s digits long.' % (len(str(prod))))print('Took %s seconds to calculate.' % (endTime - startTime))
```
#### The time.sleep() Function

* This function allows you to pause your programs for a set time.
* This is a blocking action - While the program is sleeping, the program cannot do any other executions

Example

```
>>> import time>>> for i in range(3):           print('Tick')           time.sleep(1)           print('Tock')           time.sleep(1)     
TickTockTickTockTickTock>>> time.sleep(5)
```

#### Rounding Numbers

* Python provides `round()`
* This will make working with time values easier 

Example

```
>>> import time>>> now = time.time() 
>>> now 
1425064108.017826>>> round(now, 2) 
1425064108.02>>> round(now, 4) 
 1425064108.0178>>> round(now) 
1425064108
```

#### DateTime Module

* Provides data and time information in cleaner format
* Also allows you to do arithmetic on dates
* To get the current date, use : `datetime.datetime.now()`
* The returned format is in `(year,month,day,hour,minute,second)`

Example

```
>>> import datetime>>> datetime.datetime.now()datetime.datetime(2015, 2, 27, 11, 10, 49, 55, 53) 
>>> dt = datetime.datetime(2015, 10, 21, 16, 29, 0) 
>>> dt.year, dt.month, dt.day(2015, 10, 21)>>> dt.hour, dt.minute, dt.second(16, 29, 0)
```

* Unix epoch timestamp can be conerted to a datetime object with `datetime.datetime.fromtimestamp()`

Example

```
#1,000,000 seconds behind the timestamp
>>> datetime.datetime.fromtimestamp(1000000) 
datetime.datetime(1970, 1, 12, 5, 46, 40)>>> datetime.datetime.fromtimestamp(time.time()) 
datetime.datetime(2015, 2, 27, 11, 13, 0, 604980)
```

Example: date time arithmetic

```

>>> halloween2015 = datetime.datetime(2015, 10, 31, 0, 0, 0)>>> newyears2016 = datetime.datetime(2016, 1, 1, 0, 0, 0) 
>>> oct31_2015 = datetime.datetime(2015, 10, 31, 0, 0, 0)>>> halloween2015 == oct31_2015 
True
# The later the time is, the greater it is. >>> halloween2015 > newyears2016 
False>>> newyears2016 > halloween2015 
True>>> newyears2016 != oct31_2015 
True
```

#### The timedelta Data Type

* This represents a duration of time rather than a moment in time
* To create a timedelta object, use `datetime.timedelta(weeks,days,hours,minutes,seconds,milliseconds,microseconds)`
* Timedelta objects represents the total duration in days,seconds and microseconds, with each of these being an attribute

Example

```
>>> delta = datetime.timedelta(days=11, hours=10, minutes=9, seconds=8)
>>> delta.days, delta.seconds, delta.microseconds(11, 36548, 0)>>> delta.total_seconds() 986948.0>>> str(delta)'11 days, 10:09:08'
```

* You can do date arithmetic on datetime values

```
>>> dt = datetime.datetime.now()>>> dtdatetime.datetime(2015, 2, 27, 18, 38, 50, 636181) >>> thousandDays = datetime.timedelta(days=1000) >>> dt + thousandDays   datetime.datetime(2017, 11, 23, 18, 38, 50, 636181)
```

#### Pausing Until a Specific Date

* `time.sleep()` will allow you to pause your program
* You can create a while loop containing `time.sleep()` to stop the program until a specific date.
* Its good practice to use `time.sleep(1)` if you are doing this. `time.sleep(1)` does not block the program while the while loop is executing

Example:

```
import datetimeimport timehalloween2016 = datetime.datetime(2016, 10, 31, 0, 0, 0)while datetime.datetime.now() < halloween2016:    time.sleep(1)
```

#### Converting datetime Objects into Strings

* This can be done by using the `strftime()` method
* This method can take the following derivates as parameters:
	* `%Y` = Year with century, as in '2014'
	* `%y` = Year without century, '00' to '99' (1970 to 2069)
	* `%m` = Month as a decimal number, '01' to '12'
	* `%B` = Full month name, as in 'November'
	* `%b` = Abbreviated month name, as in 'Nov'
	* `%d` = Day of the month, '01' to '31' 
	* `%j` = Day of the year, '001' to '366'
	* `%w` = Day of the week, '0' (Sunday) to '6' (Saturday)
	* `%A` = Full weekday name, as in 'Monday'
	* `%a` = Abbreviated weekday name, as in 'Mon'
	* `%H` = Hour (24-hour clock), '00' to '23'
	* `%I` = Hour (12-hour clock), '01' to '12'
	* `%M` = Minute, '00' to '59'
	* `%S` = Second, '00' to '59'
	* `%p` = 'AM' or 'PM'
	* `%%` = Literal '%' character

Example

```
>>> oct21st = datetime.datetime(2015, 10, 21, 16, 29, 0) 
>>> oct21st.strftime('%Y/%m/%d %H:%M:%S')'2015/10/21 16:29:00'>>> oct21st.strftime('%I:%M %p')'04:29 PM'>>> oct21st.strftime("%B of '%y") 
>>> "October of '15"
```

#### Converting Strings into datetime Objects

* Use `strptime(string,deritives)`

Example

```
>>> datetime.datetime.strptime('October 21, 2015', '%B %d, %Y') datetime.datetime(2015, 10, 21, 0, 0)>>> datetime.datetime.strptime('2015/10/21 16:29:00', '%Y/%m/%d %H:%M:%S') datetime.datetime(2015, 10, 21, 16, 29)>>> datetime.datetime.strptime("October of '15", "%B of '%y") datetime.datetime(2015, 10, 1, 0, 0)>>> datetime.datetime.strptime("November of '63", "%B of '%y") datetime.datetime(2063, 11, 1, 0, 0)
```

#### Multithreading

* Thread module allows you to do multithreading
* To create a thread, use: `threading.Thread(target=methodNameHere)`
* the target should be whatever method you want the thread to run when the thread is started
* Note that a python program will not terminate until all threads have terminated

Example

```
 import threading, time      print('Start of program.')def takeANap(): time.sleep(5)print('Wake up!')threadObj = threading.Thread(target=takeANap)threadObj.start() print('End of program.')
```

#### Passing Arguments to the Thread's Target Function

* You do this by using `args=[x,y,z]` in the `threading.thread` parameters
* If you want to pass keyword arguments, you can use `kwargs={'argument':'value'}`

Example

```
>>> import threading>>> threadObj = threading.Thread(target=print, args=['Cats', 'Dogs', 'Frogs'], kwargs={'sep': ' & '})>>> threadObj.start()Cats & Dogs & Frogs
```

#### Launching Other Programs from Python.

* `Popen()` is a built in function that can be used to open other programs
* It takes the filename as its arguments

Windows example

```
>>> import subprocess>>> subprocess.Popen('C:\\Windows\\System32\\calc.exe') <subprocess.Popen object at 0x0000000003055A58>
```

Linux example

```
>>> import subprocess>>> subprocess.Popen('/usr/bin/gnome-calculator') <subprocess.Popen object at 0x7f2bcf93b20
```

* `poll()` can be used on a subprocess to check whether it has been finished or not
* If it has not finished, it will return `None`
* If it has finished, it will return a integer exit code
* `wait()` method will block the method from completing until another process has terminated 

Example

```
>>> calcProc = subprocess.Popen('c:\\Windows\\System32\\calc.exe') 
>>> calcProc.poll() == NoneTrue
#Returned 0, meaning that the program has closed>>> calcProc.wait()0>>> calcProc.poll() 
>>> 0
```

#### Passing Command Line Arguments to Popen()

* To do this, you pass a list of arguments to `Popen()`
* The first string in the list needs to be the executable filename of the program you want to launch.
* Everything else are command line arguments


Example

```
>>> subprocess.Popen(['C:\\Windows\\notepad.exe', 'C:\\hello.txt']) 
<subprocess.Popen object at 0x00000000032DCEB8>
```

#### Task Scheduler, launchd, and cron

* These are build in schedulers for various operating systems. 
* Should take advantage of these rather than writing your own clock-checking code.

#### Opening Websites With Python

* `webbrowser.open()` function can launch a webbrowser from your program rather than opening the browser application.

#### Running Other Python Scripts

* Pass the python executable to `Popen(), along with the file name of the .py script

Example

```
>>> subprocess.Popen(['C:\\python34\\python.exe', 'hello.py']) 
<subprocess.Popen object at 0x000000000331CF28>
```

#### Opening Files with Default Applications

* Each OS has their own program that will open default files.
	* Windows = `start`
	* OSx = `open`
	* Linux = `see`
* To open a file in a default program, pass either `start`, `open` or `see` to `Popen()`

Windows Example

```
>>> fileObj = open('hello.txt', 'w') >>> fileObj.write('Hello world!')12

>>> fileObj.close()>>> import subprocess
# Uses start on windows to open the program>>> subprocess.Popen(['start', 'hello.txt'], shell=True)
```

Mac Example

```
>>> subprocess.Popen(['open', '/Applications/Calculator.app/']) 
>>> <subprocess.Popen object at 0x10202ff98>
```


--
### Sending Email and Text Mesages

#### SMTP

* Simple Mail Transfer Protocol (STMP) - Used for sending email

#### Sending Emails

* Have functions that are used for each step of sending an email

Example

```
>>> import smtplib>>> smtpObj = smtplib.SMTP('smtp.example.com', 587)>>> smtpObj.ehlo()(250, b'mx.example.com at your service, [216.172.148.131]\nSIZE 35882577\ n8BITMIME\nSTARTTLS\nENHANCEDSTATUSCODES\nCHUNKING')>>> smtpObj.starttls()(220, b'2.0.0 Ready to start TLS')>>> smtpObj.login('bob@example.com', 'MY_SECRET_PASSWORD')(235, b'2.7.0 Accepted')>>> smtpObj.sendmail('bob@example.com', 'alice@example.com', 'Subject: So long.\nDear Alice, so long and thanks for all the fish. Sincerely, Bob') {}>>> smtpObj.quit()(221, b'2.0.0 closing connection ko10sm23097611pbd.52 - gsmtp')
```

#### Connecting to an SMTP Server

* This is the server that your internet provider uses to send mail
* Here are the following STMP server domain names
	* Gmail = `smtp.gmail.com`
	* Outlook.com/Hotmail.com = `smtp-mail.outlook.com`
	* Yahoo Mail = `smtp.mail.yahoo.com`
 	* AT&T = `smpt.mail.att.net (port 465)`
	* Comcast = `smtp.comcast.net`
	* Verizion = `smtp.verizon.net (port 465)`
* You then need to create a SMTP object by using `smptlib.SMTP()`, using the domain name as a string arugment
* the SMTP object represents a connection to the server, with methods for sending emails.

Example

```
>>> smtpObj = smtplib.SMTP('smtp.gmail.com', 587) >>> type(smtpObj)<class 'smtplib.SMTP'>
```
	
* You also need to know what encryption the server  is using, and will need to call either `smtplib.SMTP()` or `smtplib.SMTP_SSL()`

#### Sending the SMTP "Hello" Message

* to ensure that the connection is working, call `ehlo()` to your smtpObject
* This should be the first method you call after getting the SMTP object, **or you will get errors**

#### Starting TLS Encryption

* If you are connecting to port 587, you need to call `starttls()` next.
* This will enable encryption for your connection.
* Port 465 already has this set up, so you do not need to worry about it.

Example

```
#If it returns 220, this means the server is ready
>>> smtpObj.starttls()(220, b'2.0.0 Ready to start TLS')
```

#### Logging in to the SMTP Server

* Use `.login(emailAddress,password)`
* Google has additional security that needs to be addressed, see `http://nostarch.com/automatestuff/` for more information

Example
```
>>>smtpObj.login('my_email_address@gmail.com', 'MY_SECRET_PASSWORD') 
(235, b'2.7.0 Accepted')
```

#### Sending an Email

* use `sendmail(yourEmailAddress,recipientEmailAddress, Body)`
* if you want to add a subject, in the email body use `Subject: .... \n`
* The return value is a dictionary, with key value pairs for email deliverys that **failed**

Example

```
>>> smtpObj.sendmail('my_email_address@gmail.com', 'recipient@example.com', 'Subject: So long.\nDear Alice, so long and thanks for all the fish. Sincerely, Bob'){}
```

#### Disconnecting from the SMTP Server

* call the `quit()` method when you have finished sending emails
* It should return the value 221, which means that the session is ending

Example

```
>>> smtpObj.quit()(221, b'2.0.0 closing connection ko10sm23097611pbd.52 - gsmtp')
```

#### IMAP

* Used to retrieve emails from the server.
* `imapclient` and `pyzmail` are the ideal modules for doing this.

#### Connecting to an IMAP Server

* Need an IMAPClient object to connect to an IMAP server and receive email.
* Each email provider will have their own IMAP server domain name
	* Gmail = `imap.gmail.com`
	* Outlook/hotmail = `imap-mail.outlook.com`
	* Yahoo = `imap.mail.yahoo.com`
	* AT&T = `imap.mail.att.net`
	* Comcast = `imap.comcast.net`
	* Verizon = `incoming.verizon.net`
* Most email providers will require SSL encryption.
	* Can add this as a parameter in `.IMAPClient()`

Example
```
>>> import imapclient>>> imapObj = imapclient.IMAPClient('imap.gmail.com', ssl=True)
```

#### Logging in to the IMAP Server

* Use `login(emailaddress,password)`
* Will return `Success` if it was successful
* Gmail will need additional information

Example

```
>>>imapObj.login('my_email_address@gmail.com', 'MY_SECRET_PASSWORD') 
'my_email_address@gmail.com Jane Doe authenticated (Success)'
```

#### Selecting a folder
* To search for email you need to select a folder first.
* Can get a list of folders by calling `list_folders()`
	* This will return a list of tuples containing information about folders

Example

```
>>> import pprint>>> pprint.pprint(imapObj.list_folders())
 [(('\\HasNoChildren',), '/', 'Drafts'), (('\\HasNoChildren',), '/', 'Filler'), (('\\HasNoChildren',), '/', 'INBOX'), (('\\HasNoChildren',), '/', 'Sent'),--snip--(('\\HasNoChildren', '\\Flagged'), '/', '[Gmail]/Starred'), (('\\HasNoChildren', '\\Trash'), '/', '[Gmail]/Trash')]
```

* to select a folder, use `select_folder(Foldername,readonly=True)`

#### Performing the Search

* Once a folder is selected, can use `.search()`
* Search takes a list of strings which are formatted to the IMAPs search keys:
	* `all` = Returns all messages in the folder. You may run in to imaplib size limits if you request all the messages in a large folder.
	* `'BEFORE date', 'ON date', 'SINCE date'` = These three search keys return, respectively, messages that were received by the IMAP server before, on, or after the given date. The date must be formatted like 05-Jul-2015. Also, while 'SINCE 05-Jul-2015' will match messages on and after July 5, 'BEFORE 05-Jul-2015' will match only mes- sages before July 5 but not on July 5 itself.
	* `'SUBJECT string', 'BODY string', 'TEXT string'` = Returns messages where string is found in the subject, body, or either, respectively. If string has spaces in it, then enclose it with double quotes: 'TEXT "search with spaces"'.
	* `'FROM string', 'TO string', 'CC string', 'BCC string'` = Returns all messages where string is found in the “from” emailaddress, “to” addresses, “cc” (carbon copy) addresses, or “bcc” (blind carbon copy) addresses, respectively. If there are multiple email addresses in string, then separate them with spaces and enclose them all with double quotes:'CC "firstcc@example.com secondcc@example.com"'.
	* `'SEEN', 'UNSEEN'` = Returns all messages with and without the \Seen flag, respec- tively. An email obtains the \Seen flag if it has been accessed with a fetch() method call (described later) or if it is clicked when you’re checking your email in an email program or web browser. It’s more common to say the email has been “read” rather than “seen,” but they mean the same thing.
	* `'ANSWERED', 'UNANSWERED'` = Returns all messages with and without the \Answered flag, respectively. A message obtains the \Answered flag when it is replied to
	* `'DELETED', 'UNDELETED'` = Returns all messages with and without the \Deleted flag, respec- tively. Email messages deleted with the delete_messages() method are given the \Deleted flag but are not permanently deleted until the expunge() method is called 
	* `'DRAFT', 'UNDRAFT'` = Returns all messages with and without the \Draft flag, respec- tively. Draft messages are usually kept in a separate Drafts folder rather than in the INBOX folder
	* `'FLAGGED', 'UNFLAGGED'`= Returns all messages with and without the \Flagged flag, respectively. This flag is usually used to mark email mes- sages as “Important” or “Urgent.”
	* `'LARGER N', 'SMALLER N'` = Returns all messages larger or smaller than N bytes, respectively.
	* `'NOT search-key'` = Returns the messages that search-key would not have returned.
	* `'OR search-key1search-key2'` = Returns the messages that match either the first or secondsearch-key.

Example Searches 

```
imapObj.search(['ALL']) 
# Returns every message in the currentlyselected folder.imapObj.search(['ON 05-Jul-2015'])
# Returns every message sent on July 5, 2015.
imapObj.search(['SINCE 01-Jan-2015', 'BEFORE 01-Feb-2015', 'UNSEEN'])# Returns every message sent in January 2015 that is unread. (Note that this means on and after January 1 and up to but not including February 1.)imapObj.search(['SINCE 01-Jan-2015', 'FROM alice@example.com']) 
# Returns every message from alice@example.com sent since the start of 2015.imapObj.search(['SINCE 01-Jan-2015', 'NOT FROM alice@example.com'])# Returns every message sent from everyone except alice@example.com since the start of 2015.imapObj.search(['OR FROM alice@example.com FROM bob@example.com']) 
# Returns every message ever sent from alice@example.com or bob@example.com.imapObj.search(['FROM alice@example.com', 'FROM bob@example.com']) 
# Trick example! This search will never return any messages, because messages must match all search keywords. Since there can be only one “from” address, it is impossible for a message to be from both alice@example.com and bob@example.com.
```
* `search()` returns unique IDs of the email rather than the email itself, as integers.
* Can then pass the ID to `fetch()` to get the email

```
>>> UIDs = imapObj.search(['SINCE 05-Jul-2015'])>>> UIDs[40032, 40033, 40034, 40035, 40036, 40037, 40038, 40039, 40040, 40041]
```

#### Size Limits

* If you create a search that matches a large amount of emails, you may get the following error: `imaplib.error: got more than 10000 bytes`
* If this does happen, you may need to disconnect and reconnnect to the server
* Alternatively, you can increase the limit by increasing`._MAXLINE`

Example

```
>>> import imaplib>>> imaplib._MAXLINE = 10000000
```
#### Fetching an Email and Marking It as Read

* to get the email, use `.fetch(UID,['BODY[]'])
* `BODY[]` tells fetch to download the body content for the emails specified in your UID List
* Can use `pprint` to print the body in a readable format

Example

```
>>> rawMessages = imapObj.fetch(UIDs, ['BODY[]'])>>> import pprint>>> pprint.pprint(rawMessages){40040: {'BODY[]': 'Delivered-To: my_email_address@gmail.com\r\n'                   'Received: by 10.76.71.167 with SMTP id '--snip--
'\r\n''------=_Part_6000970_707736290.1404819487066--\r\n',
# Sequence number (Similar to UID)'SEQ': 5430}}
```
* If you want to mark the email as read, change `readonly=True` in `select_folder` to `readonly=False`

Example

```
>>> imapObj.select_folder('INBOX', readonly=False)
```

#### Getting Email Addresses from a Raw Message

* Pyzmail can parse raw messages and return PyzMessage objects.
* You do this by passing the rawMessages to `PyzMessage.factory`

Example

```
>>> import pyzmail>>> message = pyzmail.PyzMessage.factory(rawMessages[40041]['BODY[]'])
```
* You can them use methods like `.get_subject()` to conveniently get the information

Example

```
>>> message.get_subject()'Hello!'>>> message.get_addresses('from')[('Edward Snowden', 'esnowden@nsa.gov')] >>> message.get_addresses('to')[(Jane Doe', 'my_email_address@gmail.com')] >>> message.get_addresses('cc')[]>>> message.get_addresses('bcc')[]
```

#### Getting the Body for a Raw Message

* If the email is only plaintext. PyzMessage object will have `html_part = nNone`
* If it is a html email, PyzMessage will have `text_part = NOne`
* If its a mix, you need to use `get_payload()` to get the email as a byte type, then use `.decode()` to parse it
	* .`decode` needs either `(text_part.charset)` or `(html_part.charset)` to it to decode it

Example

```
>>> message.text_part != None True>>> message.text_part.get_payload().decode(message.text_part.charset) 
 'So long, and thanks for all the fish!\r\n\r\n-Al\r\n'>>> message.html_part != NoneTrue
>>>message.html_part.get_payload().decode(message.html_part.charset)'<div dir="ltr"><div>So long, and thanks for all the fish!<br><br></div>-Al <br></div>\r\n'
```

#### Deleting Emails

* Need to pass the UID to `.delete_messages()` with `\\Deleted` as a parameter
* Once you have deleted, you need to call `.expunge()` to perminantly remove it

Example

```
>>> imapObj.select_folder('INBOX', readonly=False) v>>> UIDs = imapObj.search(['ON 09-Jul-2015'])>>> UIDs[40066]>>> imapObj.delete_messages(UIDs)w{40066: ('\\Seen', '\\Deleted')} 
>>> imapObj.expunge() 
>>> ('Success', [(5452, 'EXISTS')])
```
#### Disconnecting from the IMAP server

* Call `.logout`

#### Text Messages

CONTINUE

--
### Manipulating Images
CONTINUE
--
### Controlling The Keyboard and mouse With GUI Automation

####  Installing  pyautogui module

* This module can send virtual keypresses and mouse clicks.
* When using GUI Automation, python may execute too fast.

Installing on windows:
No other dependancies needed
Installing on OSX
```
sudo pip3 install pyobjc-framework-Quartz, sudo pip3install pyobjc-core, and then sudo pip3 install pyobjc.
```
Installing on Linux:
```
sudo pip3 install python3-xlib, sudo apt-get install scrot, sudo apt-get install python3-tk, and sudo apt-get install python3-dev.
```

#### Shutting Down Everything by Logging out
* On windows and Linux, use `CTRl-ALT-DEL`
* On OSX, use ` COMMAND-SHIFT-OPTION-Q`

#### Pauses and Fail-Safes

* Can tell your script to wait after every function call, which will give you a short time to control the mouse and keyboard if something goes wrong.
* YOu do this by assigning the number of seconds you it to puase to `pyautogui.PAUSE`
* You can also enable a failsafe feature. If you move your mouse to the top left corner of the screen, the program will terminate. 
* You can enable this by assigning `pyautogui.FAILSAFE = True`

Example

```
>>> import pyautogui>>> pyautogui.PAUSE = 1>>> pyautogui.FAILSAFE = True
```

#### Controlling Mouse Movement

* Mouse functions of PyAutoGUI use x and y coordinates.
* For a 1902x1080 resolution:
	* Top left corner of screen = 0,0
	* Top Right corner of screen = 1919,0
	* Bottom left corner of screen = 0,1079
	* Bottom right corner of screen = 1919,1070
* You can get your resolution by caling `pyautogui.size()`
* You can also assign variables to hold the width and height of your screen by doing: ` width, height = pyautogui.size()`

#### Moving the Mouse

* `zpyautogui,moveTo(x,y,duration=x)` will move the mouse to the specified coordinates.
* Duration can be used to specify how long it should take to move the mouse to that position
* Duration is optional, if you leave it out, it will move instantly

Example

```
>>> import pyautogui >>> for i in range(10):      pyautogui.moveTo(100, 100, duration=0.25)      pyautogui.moveTo(200, 100, duration=0.25)      pyautogui.moveTo(200, 200, duration=0.25)      pyautogui.moveTo(100, 200, duration=0.25)
```

* pyautogui.moveRel() moves the mouse cursor relative to its current positon.

Example

```
>>> import pyautogui >>> for i in range(10):      pyautogui.moveRel(100, 0, duration=0.25)      pyautogui.moveRel(0, 100, duration=0.25)
      pyautogui.moveRel(-100, 0, duration=0.25)                   				pyautogui.moveRel(0, -100, duration=0.25)
```

#### Getting the Mouse Position

* Can getermine the mouse's current position by calling `pyautogui.position()`
* This will return a tuple containg the x and y values respectively
*
Example

```
>>> pyautogui.position() 
(311, 622)>>> pyautogui.position() 
(377, 481)>>> pyautogui.position() 
(1536, 637)
```

#### Clicking the Mouse

* `pyautogui.click(x,y,button=z)`
* By default this will left click
* To right click, use `button='right'`

Example

```
>>> import pyautogui>>> pyautogui.click(10, 5)
```

* Alternatively, you can use `pyauto.mouseDown()` followed by `pyauto.mouseUp()`
* Here are more useful mouse clicking methods:
	* `.doubleClick()`
	* `.rightClick()`
	* `.middleClick()`

#### Dragging the Mouse

* Can use the following:
	* `.dragTo(x,y,duration=z)`
	* `.dragRel(x,y,duration=z)`
	* `.moveTo(x,y,duration=z)`
	* `.moveRel(x,y,duration=z)`

#### Scrolling the Mouse

* `.scroll(numberOfTimesToScroll)`

#### Getting a screenshot

* `.screenshot()`

```
>>> import pyautogui>>> im = pyautogui.screenshot()```

#### Sending a String from the Keyboard

* `typewrite()` sends virtual kep presses.
* Its important to click on where you want the text to go first. 

Example (Important to keep them on the same line to rpevent python from prompting you!)

```
>>> pyautogui.click(100, 100); pyautogui.typewrite('Hello world!')
```

* By default python will enter all the text instantly. To add a wait add a float value as a second parameter to `typewrite`

#### Key Names
* Instead of using a string, you can pass a list of keys
* This will press the keys in the order they are in the list

Example

```
>>> pyautogui.typewrite(['a', 'b', 'left', 'left', 'X', 'Y'])
```

* Some keys have special attributes
* Below is a list:
	* `'a', 'b', 'c', 'A', 'B', 'C', '1', '2', '3', '!', '@', '#', and so on` = Keys for single characters
	* `'enter' (or 'return' or '\n')` = The ENTER key
	* `'esc'` = The ESC key
	* `'shiftleft', 'shiftright'` = The left and right SHIFT keys
	* `'altleft', 'altright'` = The left and right ALT keys
	* `'ctrlleft', 'ctrlright'` = The left and right CTRL keys
	* `'tab' (or '\t')` = The TAB key
	* `'backspace', 'delete'` = The BACKSPACE and DELETE keys
	* `'pageup', 'pagedown'` = The PAGE UP and PAGE DOWN keys
	* `'home', 'end'` = The HOME and END keys
	* `'up', 'down', 'left', 'right'` = The up, down, left, and right arrow keys
	* `'f1', 'f2', 'f3', and so on` = The F1 to F12 keys	* `'volumemute', 'volumedown', 'volumeup'` = The mute, volume down, and volume up keys (some keyboards do not have these keys, but your operating system will still be able to understand these simulated keypresses)
	* `'pause'` = The PAUSE key
	* `'capslock', 'numlock', 'scrolllock'` = The CAPS LOCK, NUM LOCK, and SCROLL LOCK keys
	* `'insert'` = The INS or INSERT key
	* `'printscreen'` = The PRTSC or PRINT SCREEN key
	* `'winleft', 'winright'` = The left and right WIN keys (on Windows)
	* `'command'` = The Command key (on OS X)
	* `'option'` = The OPTION key (on OS X)

#### Pressing and Releasing the Keyboard key

* `.keyDown(key)` and `'.keyUp(key)` 
* Can press other keys while the key is down

Example

```
>>> pyautogui.keyDown('shift'); pyautogui.press('4'); pyautogui.keyUp('shift')
```

#### Hotkey Combinations

* Can use `.hotkey(key1,key2..)` to do hotkey commands (Such as copy/paste)

Example

```
>>> import pyautogui, time >>> def commentAfterDelay():      pyautogui.click(100, 100)      pyautogui.typewrite('In IDLE, Alt-3 comments out a line.')      time.sleep(2)      pyautogui.hotkey('alt', '3')>>> commentAfterDelay()
```

--
## Running Programs

### In Windows

* conventiat to create a .bat batch file for running your program.
* Inside the .bat file, have  the following line only:

`@py.exe C:\path\to\script.py %*`

### For OSX and Linux

* Make it executable by using `chmod +x pythonScript.py` in terminal
* Entering `./pythonScript.py` will allow you to run it in the terminal
