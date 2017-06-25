# Beginning Ruby From Novice To Professional - Peter Cooper

NB this is notes from the developer primer at the end of the book. 

## The Basics

### Definitions and Concepts

* Has automatic garbage collection
* Mostly portable
* Supports multitasking natively and through "green" threads
* has large standard library
* Supports dynamic language features (Closures, iterators, exceptions, overloading and reflection)
* Is an interpreted language, compiled down into platofrm independent bytecode that is ran by a virtual machine
* Almost everything in Ruby is treated as an object

### The Ruby Interpreter and Running Ruby Code

* Running a Ruby script is done by `ruby name_of_script.rb`
* The ruby interpreter has a number of options.
	* `ruby -v` gets the version

### Interactive Ruby

* There is an interactive Ruby interpreter called IRB
* Allows you to write Ruby code in an immediate, interactive environment where the results are shown as soon as you type it

```
irb 
4+4

```

### Expressions and Flow Control

#### Basic Expressions

* Can assign the results of expressions to variables 
* Method calls, variables, literals, brackets and operators can all combine so long as subexpressions always feed values of the correct type into their parent expressions or provide methods that allow them to be coerced into the right types

#### Class Mismatches

* Objects are not convered between different classes automatically.

Eg, this will not work:

` "10" + 20 `

* You Can only use objects that are of the same class or that support automatic translation between classes (coercion) in operations with one another (methods to do this are generalled of the name `to_x`

Example

` "20" + 10.to_s`

#### Comparison Expressions

* x==y
* x && y
* ||
* !=
* !(x==y)

#### Branching and Conditional Execution

* Simplest form of conditonal execution is with a single line using `if` or `unless`

` puts "The universe is broken!" if 2==2`

* This will print the string
* If performs the comparison before the rest of the line is executed
* Multi line ifs are also supported

```
if 2==2
puts "the univese is broken!"
end

```

* needs a end on the last line

```
if 2==2
puts "Hello"
else 
puts "world"
end
```

#### The Ternary Operator (Conditional Expressions)


` expression ? true_expression : false_expression`

Example

```
x = 10
puts x > 10? "higher than ten" : "Lower or equal to ten"
```

#### Loops CONTINUE (Chapter 3)

* Supports:
	* While
	* loop
	* until 
	* next
	* break

### Object Orientation

#### Objects

* Everything is an object
* You can call methods on almost everything, and chain methods together

``` something.function3.function2.function1```

* function 1 is called first, then 2, then 3 (Right to left)

#### Classes and Methods

Example

```
class Person
def initalize(name,age)
	@name = name
	@age = age
end

def name 
return @name
end

def age
return @age
end
end

```

* Initalize method is called automatically when you create a new instance of the class
* The two parameters are accepted and are variables assoicated with a particular instance of a class and begin with "@" (@name is equivlent to this.name in java!)

Creating objects

```
person1= Person.new('chris',25)
person2 = Person.new('bob' , 24)
//printing data
puts person1.name
puts person2.age
```

* You can add features to classes even if they have already be defined
* You do this by 'reopening' classes and adding more features

Example

```
class Person
def name=(new_name)
	@name = new_name
end

def age=(new_age)
	@age = new_age
end
end
```

* These two new methods are added to the person class and are automatically made aviable to all  existing instances of the class
* Our example the above methods are setter methods, as signifed by the equals sign following their names
* This allows us to:

```
person1.name="Barney"
person2.age =101
puts person1.name
puts person2.age
```

* Ruby also provides the `attr_accessor` helper method. This method automatically creates accessors and setter methods within a class for you

```
class Person
attr_accessor :name, :age
end
```

* To create methods that can only be used on that specific clas, use `@@` to define class variables and `self.x` to define class methods

eg

```
class Person
@@count = 0

def initalize
//this is a class variable
@@ count +=1
end

//this is a class method
def self.count
@@count
end
end
```


### Method Visibility

* Methods are public by default
* Can have private and protected methods


```
class MyClass
def public_method
end

private
def private_method1
end

def private_method2
end

protected 
def protected_method
end
end

```

* You have the option to explicity set methods to be private/public/protected after they are defined by doing this at the **END** of the class

```
class MyClass
def public_method
end

def private_method1
end

def private_method2
end

def protected_method
end

public :public_method
private :private_method1, :private_method2
protected :protected_method
end
```

## Data

* We have the following types:
	* Strings
	* Regular Expressions
	* Numbers (Ints, floats)
	* Arrays (Can store a mixture of types in each array)
	* Hashes (Associative arrays, can only store the same type per array)


## Input/Output

Types of I/O available:

* Files
* Databases
* Websites