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

### Working With Excel Spreadsheets

**CONTINUE**

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


### Working with CSV Files and JSON Data

CONTINUE

### Keeping Time, Scheduling Tasks, and Launching Programs
CONTINUE

### Sending Email and Text Mesages
CONTINUE

### Manipulating Images
CONTINUE

### Controlling The Keyboard and mouse With GUI Automation
CONTINUE

## Running Programs

### In Windows

* conventiat to create a .bat batch file for running your program.
* Inside the .bat file, have  the following line only:

`@py.exe C:\path\to\script.py %*`

### For OSX and Linux

* Make it executable by using `chmod +x pythonScript.py` in terminal
* Entering `./pythonScript.py` will allow you to run it in the terminal
