# The Ruby Programming Language


```
You should use a scripting language when speed of development is more important than speed of execution.
```
## The Structure and Execution of Ruby Programs

### Lexical Structure

* Ruby interpreter parses a program as a sequence of tokens

#### Comments

* Done with the `# comment here`

#### Embedded Documents

* These are form of multi line comments
* Uses `# =begin` and `# =end`
* Must have the space between `#` and `=`

Example

```
# =begin
	this will be commented out
# =end
```

#### Literals

* Values that apear directly in Ruby source code
* These include:
	* Numbers (1 or 1.0)
	* Strings	('hello' or "hello")
	* Regular expressions (/three/)

#### Identifiers

* Simply a name
* These are used for identifying classes, variables, methods ect
* Can consist of:
	* Letters
	* Numbers
	* Underscores
* Cannot consist of numbers or have white space/non printing characters
* **Constants begin with capitals**
* **Classes and module names must beginin with capitals**

#### Punctuation in Identifiers

* Can appear at the start and end of ruby identifiers
* These are the most commmon:
	* `$` = Global variables 
	* `@` = Instance vairables
	* `@@` =  Class variables
	* `?` = Placed at the end of a method name to represent a boolean return value
	* `!` = places at the beginining of a method name. Used to distinguish mutator methods 
	* `=` = placed at the end of a method name, allows this method to beinvoked by assignment

	
Example

```
$files			#A global variable	
@data			#An instance variable
@@counter		#A class variable
empty?			#A Boolean-valued method or predicate
sort!			#An in-place alternative to the regular sort method
timeout=		#A method invoked by assignment
```

#### Newlines as statement terminators

* Where java uses `;` to terminate statements, Ruby uses **New lines**
* In Ruby 1.9, if the first non space character on a line is `.`, this is thought of as an continuation statement
* General guidelines:
	* Never put a space between a method name and the opening parenthesis
	* If the first argument to a method begins with an open parenthesis, always use parentheses in the method invocation (Eg write f((3+2)+1)
	* Always run the Ruby interpreter with the -w option so it will warn you if you forget either of the rules above!

### Syntactic Structure

* Numbers and strings can be one of the following:
	* true
	* false
	* nil
	* self
* Complex values can be written as the following compound expressions:
	* [1,2,3] (array
	*  {1=>"one", 2=>"two"} (Hash)
	*  1..3 (range)
* Expressions are done via indentation
* Expressions end with `end` keyword
* This is done for classes, methods, modules ect....

examples

```
if x < 10 then
	x = x + 1
end

while x < 10 do 
	print x
	x = x + 1
end
```

#### File Structure

* must include a "shebang" comment at the top of the file to say howt o execute the code
* If the program contains a coding comment, this must be on the first line, or second line if there is a shebang comment
* Each file must contain a line that has the token `__END__` with no whitespace before or after

Example

```
#!/usr/bin/ruby -w      shebang comment
# -*- coding: utf-8 -*- coding comment
require 'socket'   load networking library... program code here__END__ 
... 	program data here
```

#### Program Encoding

* By default the interpreter assumes the source code is encoded in ASCII

#### Specifying encoding

```
coding: utf-8
```

### Program Execution

* Rememeber that ruby is a scripting language
* By default ruby script will be executed sequentially, in the order that they appear 
* There is no main method as in static compiled langauges
* The Ruby interpreter is invoked from the command line and given a script to execute.
* When a file is passed to the interpreter, it first executes the `BEGIN` blocks, then starts at the first line until one of the following happens:
	* It executes a statement that caues the ruby program to terminate
	* It reaches the end of the file
	* It reads a line that marks the logical end of the file with the token `__END__`


## Datatypes and Objects


* Numeric types:
	* Integer
		* Fixnum
		* Bignum
	* Float
	* Complex
	* BigDecimal
	* Rational
* Text (Note these are need to escaped and so on...)
	* Single quoted string literals ('eg'
	* Double-quoted string literals ("Eg")
	* Chracter literals (You preceed the character with a question mark (?A))
* Arrays
* Hashes
* 

