# Python For The Busy Java Developer - Deepak Sarda

[Website](https://antrix.net/static/pages/python-for-java/online/)
---------

## The Syntax

* Creating A list: `numbers = [1,2,3,4]` or numbers = []
* For loop & if Statements:
``` 
for num in numbers:
	if num & 2 != 0:
		numbers.append(10)
```
* Everything uses indendation

------

## Basic Types

* Numbers
	* Int
	* Long
	* Float
	* Complex
* Strings
	* Str (Eg, 'abc')
	* unicode
	* str (eg, 'C:/temp')
* Collections
	* List ['apple','ball']
		* Equivlent to arraylists in java
	* Tuple ('apple','ball','car')
		* Tuples are immutable
	* dict {'fruit':'apple','toy':'ball'}
		* Same as hashmap in java
	* Set {'apple','ball'}
		Same as hashset in java
* Collections types can hold values of different data types


## List Comprehensions

* Allows you do functional one liners instead of complicated if statements
* Eg ` factorials =  map(math.factorial,range(5))
* Can think of it as `factorials = [math.factorial(num) for num in range(5)]

## Functions

* Objects can live without classes. 
	* Can be created at run time
	* assigned to variables
	* pased as arguments to other functions
	* returned as values from other functions
* Suppots anonymous functions in the form of lambda expressions
* Syntax:

```
def a_function(arg1, arg2="default", *args, **kwargs):
    """This is a short piece of documentation for this function.
       It can span multiple lines.
    """
    print "arg1:", arg1     # arg1 is a mandatory parameter
    print "arg2:", arg2     # arg2 is an optional parameter with a default value
    print "args:", args     # args is a tuple of positional parameters
    print "kwargs:", kwargs # kwargs is a dictionary of keyword parameters

```

* Functions begin with `def` and are followed with parameters
* No curly braces, indentation is used instead
* Ignore the * in the function parameters for now, will be exaplined later
* Dont have to declare types for function parameters (Relies on duck typing)
* Can set default values for arguments(our example is arg2)
* Order is not important when you assign values to the names of the parameters in a function call

` a_function(arg2="twenty", arg1=10, arg3=30, arg4="forty")`

## Functions and Tuples

* Can return mutliple values in the form of a tuple
* Example:

```
def multi_return():
    # These are automatically wrapped up
    # and returned in one tuple
    return 10, 20, 'thirty'

>>> values = multi_return()
>>> print values
(10, 20, 'thirty')
```

* This is done by unpacking
* Unpacking is where it assigns values from left to right
` a, b, c = multi_return()`
* Above will assign the first value from multi_return() to a, second to b, and third to c
* This only works if the number of variables you are assigning the to the function are equal to the number of values you want to return
* `*x` is notation to tell python to unpack the tuple values into a tuple

```
>>> ternary(1, 2, 3)
1 2 3

>>> args = (1, 2, 3)
>>> ternary(args)
TypeError: ternary() takes exactly 3 arguments (1 given)

>>> ternary(*args)  # Unpacks the args tuple before function call
1 2 3
```
* `**x` unpacks dict values

```
>>> kwargs = {'a': 1, 'b': 2, 'c': 3}
>>> ternary(kwargs)
TypeError: ternary() takes exactly 3 arguments (1 given)

>>> ternary(**kwargs) # unpacks the dictionary before function call
1 2 3
```

## Functions Inside Functions

```
def make_function(parity):                                            
    if parity is 'even':
        matches_parity = lambda x: x % 2 == 0                         
    elif parity is 'odd':
        matches_parity = lambda x: x % 2 != 0
    else:
        raise AttributeError("Unknown Parity: " + parity)             

    def get_by_parity(numbers):                                       
        filtered = [num for num in numbers if matches_parity(num)]
        return filtered

    return get_by_parity 
```

* use the lambda keyword to create lambdas
* Can have nested functions (Our example has get_by_partity)
* Functions are treated as first-class objects of type function
* Can be passed * assign to variables like any object

## Classes

* everything in python is a object

```
class Person(object):
    def __init__(self, first, last):
        self.first = first
        self.last = last

    def full_name(self):
        return "%s %s" % (self.first, self.last)

    def __str__(self):
        return "Person: " + self.full_name()
```
 * Object has to be explicit in Python in the class defintions parameters
 * If using inheritance, the classname of the parent class is passed into the parameters of the class
 * `__init__` All fields/attributes are initalized by the init method (Pretty much the java constructor)
 * All instance methods must pass `self`. This is equivilent to `this` in java

```
 
 >>> person = Person('Clark', 'Kent')  

>>> print person                      
Person: Clark Kent

>>> print person.first                
Clark

>>> print person.full_name()          
Clark Kent

>>> print Person.full_name(person)    
Clark Kent

```

* Object creation is line one above
* attrivutes are accessed using dotted syntax (line 3)
* Methods are done by dotted syntax too, even though self is in the definition, it does not need to be passed (This is done for you)
* You can however pass your version of self (line 5)

## Inheritance
 
 ```
 class SuperHero(Person):
    def __init__(self, first, last, nick):
        super(SuperHero, self).__init__(first, last)
        self.nick = nick

    def nick_name(self):
        return "I am %s" % self.nick
 ```
 
 * Allowed multiple inheritance and single inheritance
 * Super is the same as in java

 

 ## Polymorhpism
 
 
 ```
 
 class Square(object):
    def draw(self, canvas):
        ...
class Circle(object):
    def draw(self, canvas):
        ...
 
 ```
 
 * This will work without a shape class, python does not need a base class

## Importing Code

```
import model.order

sell_order = order.SellOrder()
```

* Import statements can only be used to import packages or modules
* If you want to access a class or function definiton, you have to use the syntax ` from <package|module >import <item>:`
* Eg: 

```
from model.order import SellOrder

sell_order = SellOrder()
```

* You can rename imports with the `as` keyword

```
from model.order import TYPES as ORDER_TYPES
from db import TYPES as DATABASE_TYPES

print ORDER_TYPES
# ['buy', 'sell']

print DATABASE_TYPES
# ['mysql', 'postgresql']
```

## The main() Method

* There is no formal application entry point inmythod
* Python executes a file when you run ` python file.py`
* Execution starts at the beginning and ends at the end
* To simulate a main method, wrap the top level functions into one function, and call that function 
* Example

```
def get_odds(numbers):
    odds = [n for n in numbers if n % 2 != 0]
    return odds

def main():
    odds_until = 10
    numbers = range(odds_until)
    print get_odds(numbers)

main()

```