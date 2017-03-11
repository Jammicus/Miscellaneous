# Javascript & JQuery - Jon Duckett

--------
## Introduction
----

### HTML Elements

* Used to describe the structure of a page. 
* Elements contain opening and closing tags, as well as its content
* Opening tags can carry attributes, which describe the element
* Attributes have a name and a value, where the value is usually put inside quotation marks.

` <p class = "fruit">peach</p>`

* Class is the attribute name
* Fruit is the attribute value
* The`<p ...>` is the opening tag
* The `</p>` is the closing tag 

### CSS Rules

* Rules indication how the conents of elements should be shown in the browser
* Each rule has a selector & declaratiion block
* Selector state which elements the rule applies to
* Declaration block states how the element should be shown
* Declaration blocks have a property, and a property value, which is denoted as  `propertyName: propertyValue`

` .fruit {color:pink} `

* The `.fruit` is the selector
* The ` {color: pink;} ` is the `property name: propery value`


---------------------

### Linking to a javascript file from an HTML Page

* You use the `<script>` element 
* The `<script>` elements `src` attribute says where to find the javascript file

``<script src = "js/add-conent.js"></script>``

* Scripts are run where they are found in the HTML

------------
### How To  Use Objects & Methods

* The format is: 
``` 
object.method(parameters)
```
----------------------------------

## Basic Javascript Instructions

-------

### Statements

* Defined as each individual step
* Eg, if statements, variable declaration....
* Each start on a new line.
* Can be organized into code blocks

### Comments

* Defined as `// comment here `
* Can have multi-line comments. These are defined as ` /* ....*/`

### Variables

* Used to hold data
* Have no explicit types in java script
* Variables that need to change value should be defined as ` var name = value`
* Variables that should not change value should be defined as ` const name = value `

### Data Types

* Vars and consts can take on 3 types
	* Numberic Data types - Handles positives, negatives and decimals
	* String data types - Handles a series of characters
	* Boolean Data types - Handles `True` or `False` values

### Rules For Naming Variables

1. The name must start with either $, _ or a chracters. **NEVER** numbers
2. You cannot use reserved words 
3. Variables are case sensitive. So `score` and `Score` are different variables
4. Use a name that describes the information that it is storing, eg `homeAddress`
5. If you have more than two words in the variable, use a captial to seperate the words, as shown in number 4.

### Arrays

* Stores a series of values.
* Should be used when you dont know how many variables will be needed, or when you need a large amount of variables.

### Creating Arrays

` var colors ;`
`colors = ['white','green','yellow'];`

### Accessing Values in Arrays

* Arrays are index based, starting at 0.
* To get the first element, its ` var firstItem=colors[0]`
* To get subsequent characters, increment the value in `[x]`.
* If you increment too far, where there is no more values in the array, you will get `index out of bounds.`

### Changing values in arryas

1. Find the index of the value you want to change.
2. Re assign the value.

` colors[1]='red'`

### Operators

* Assignment operators =  Assigning a value to a variable
	* Eg, ` color = 'red';`
* Arithmetic operators = Performs basic maths
	* Eg,`sum = 5+12;`
*  String operators = Combines two strings
	* Eg, ` happyBirthday  = 'Happy' + 'Birthday';`
* Comparison Operators = Checks whether it is true or false
	* Eg, ` buy = 3>5`
* Logical operators  = Combines various things to return `true` or `false`
	* Eg, `buy = (5>3) && (2<4)

### Arithmetic Operators

|Name              | Operator| Purpose                                                            | 
|--------------|----------|--------------------------------------------|
|Addition          | ``+``     | Addes one value to another                           |
|Subtraction    | ``-``      | Subtracts one value from another                 | 
|Divison           | ``/``       | Divides two values                                          |
|Multiplication |``*``       | Multiplies two values                                       |
|Increment       |``+``      | Adds one to current number                           |  
|Decrement     |``--``     | Subtracts one from the current number         |
|Modulus         |``%``      | Divdes two values and returns the remainder|

* The order of execution is BIDMAS (Brackets, INdices, Divison,Multiplcation, Addition and Subtraction)


### String Operator

* Used to join two strings together, known as concatenation
	* Eg, ``fullname = 'james'+'walter';``

### Summary of Basic Javascript Instructions

*  Scripts are made up of a series of statements. Like a cooking recipe
* Variables are used to store pieces of information used in scripts
* Arrays store more than one piece of information
* Variables can be strings, numbers or true/false values

--------------------------

## Functions, Methods & Objects

-------

### Functions

* A group of instructions 
* Can use parameters, which are given to the function work with
* When the function is finished, it will give you a value
* Asking the function to run is known as calling the function

### Declaring a Function

``` function addTwoNumbers(numberOne,numberTwo){
return x+y
}```

* The name of the function is `` addTwoNumbers`` 
* The parameters are   `` numberOne,numberTwo``
* The function when run will give back the value of `` x+y``
* to call the function, you will say ``addTwoNumbers(10,5)``
* You can pass variables to a  function, `` addTwoNumbers(aNumber,anotherNumber)``

### Getting A Single Value Out Of a Function

*  You do this by assigning the value to a variable

``` var sumOfThreeAndFive = sum(3,5) ```

### Getting Multiple Values Out Of a Function
* Done by using an array
* You define the return statement as a variable that returns an array
* When calling the function, you define which value from the array you want back

```
 	function getSize(width, height, depth) {
	var area = witdh, height;
	var volume = width* height * depth;
	var sizes = [area, volume];
	return sizes;
	} 
	
	var areaOne = getSize(3,2,3)[0];
	var volumeOne = getSize(3,2,3)[1];
```
### Anonymous Functions & Function Expressions
	
* Anonymous functions are functions with no names. 
* These are typically assigned when declaring a variable
* The function is not used until the interpreter gets to the statement.
* This function cannot be called until the interpreter finds it

	```
	var area = function(width,height) {
	return width *  height;
	};

	var size = area(3,4);
	
	```

### Immediately Invoked Function Expressions

* These are pronouced `` IIFE``
* These functions are not given a name, and are only executed once the interpreter comes across them
* at the end of the function, you will have ``()`` this tells the interpret that this should be called immediately.
* You need to wrap the function is ``( )`` to ensure that the interpret treats this function as an expression

```
var area = ( function() {
var width =3;
var height =2;
return width * height ;
} () ) ;
```

### When To Use Anonymous Functions and IIFES

* For code that only needs to be run once within a task, rather than repeatedly being called by other parts of the script. Eg:
	* As an argument when a function is called
	* To assign the value of a property to an ojbect
	* In event handlers and listenings to do something when the event occurs
	* To prevent conflicts between two scripts that might use the same variable name

### Variable Scope

* Local variables (Ones defined in function) -  can only be used in that function
* Global variables (Onces defined outside of functions) can be called in any function
* Global variables values are not changed with each function call, unless you modifiy the value in the function
* Local variables change values for each function call. (They are initalised when the function is called.

``` 
function getArea (width, height){
var area = width * height;
return area;
}
var wallSize =  getArea (3,2);
var othetWallSize = getArea(4,2);

```

* wallSize and otherWallSize are global variables
* area is a local variable, its value changes when wallSize and otherWallSize calls get area

### What are Objects?

* A series of variabless that are contained together.
* A item that a function can be called on to modify its variables. These functions are called methods

### Creating objects: Literal Notation

``` 
var hotel = {
name : 'James',
rooms: '40'
booked: 25,
checkAvailability: function() {
	return this.rooms -  this.booked;
	}
};
```

### Acessing objects

* To get values from the object, or call methods on an object, we use dot notation
* This is done by `` object.variable`` or ``object.method()``

``` 
var hotelName = hotel.name;
var roomsFree = hotel.checkAvailability();
```

### Creating Objects: Constructor Notation

* Done by using the `` new `` Keyword
* You first declare the variable as a new object `` var hotel = new Object()``
* You then can define variables and methods using the dot notation mentioned above

``` 
var hotel = new Object();

	hotel.name = 'Quay';
	hotel.rooms = 40;
	hotel.booked = 25;
	
	hotel.checkAvailability = function () {
		return this.rooms -this.booked;
	};
	
```

* The `this` notation references the specific object in questions variable values. 

### Updating an Object

* done by dot notation

```
hotel.name = 'park';

```
### Deleting a objects variable

* done by delete keyword

```
delete hotel.name;

```

### Creating Many Objects.

* We create a function with the objects variables and methods

``` 
function hotel (name, rooms, booked) {
	this.name = name;
	this.rooms = rooms;
	this.booked = booked;
	
	this.checkAvailability = function() {
	return this. rooms - this.booked;
	};
	};
```

* You then create variables and use the `new` keyword with suitable parameters

```
var seaSideHotel = new hotel("sea side hotel", 52, 25);
var cityHotel =  new hotel("City hotel",22,12);
```

### Recap: Ways of creating objects

**Creating the object then addig properties and methods.**

**Literal Notation**

```
var hotel = {}

hotel.name = 'Quay';
hotel.rooms = 40;
hotel. booked =25;

hotel.checkAvailablity = function(){
	return this.rooms-this.booked;
	};
	
```

**Object Constructor Notation**

```
var hotel = new Object();

hotel.name = 'Quay';
hotel.rooms =40;
hotel.booked = 25;
hotel.checkAvailability = function () {
	return this.rooms - this.booked;
};

```

**Creating an object with Properties and methods**

**Literal Notation**

```
var hotel = {
	name: 'quay',
	rooms : 40,
	booked: 25,
	checkAvailability: function() {
		return this.rooms - this.booked;
		}
	};
	
```

**Object Constructor Notation**

```
function Hotel(name, rooms, booked) {
	this.name = name;
	this.rooms = rooms;
	this.booked = booked;
	this.checkAvailability = function () {
		return this.rooms - this.booked;
		};
		}
	var quayHotel = new Hotel ('Quay', 40,25);
	var parkHotel = new Hotel ('Park', 120, 77);
	
```

### This Keyword

* Where a function is declared alters what this means
* This will always refer to one object

#### A functon in Global Scope Function

* When a functon is not declared within a object or function
* Will return the value of that object.

```
function windowSize() {
	var width = this.innerWidth;
	var height =  this.innerHeight;
	return [height,width];
```

#### Global Variables

* All global variables become properties of an object.
* When a function is in the global context, you can access global variables.

``` 
var width =600;
		var shape = { width:300};
		
		var showWidth = function() {
		// this will reference width declared at the top of the page
			document.write(this.width);
			};
			
			showWidth()
```

### Method of An Object

* When a function is defined inside an object, it becomes a method, this referes to the object containing it.

```
var shape = {

width:600;
height: 400;
getArea : function() {
	//refers the the variables defined above
	return this.width * this.height;
}
}
```

### Function Expression As A Method

* Referes the the passed value.

``` 
		var width = 600;
		var shape = {width: 300};
		
		var showWidth = function() {
			document.write(this.width);
		};
		
		//this uses the width value defined in shape. (Second line)
		shape.getWidth = showWidth;
		shape.getWitdth();

```

###  Arrrays are Objects

* Special type of objects.
* These hold a set of data in a key/value format.
* The index is the key (First value = index 0, second value = index 1 and so on..)

```
costs = [ 420,222,333,111];

```
### Arrays of Objects & Objects In Arrays

* Can combine arrays and objects to create complex data structures.
* Arrays can store a series of objects
* Objects can also hold arrays as values of their properties.

**Arrays in an Object**

Given this array called costs:

|Propery| Value                 |
|--------|----------------|
|room1 |items[420,40,10]|

```
//To access room 1s first value you would use the following:
costs.room1.items[0];
```
**Objects in Arrays**

Given this array called costs:

|Index Number| Value                                         |
|--------------|-------------------------------|
|0                     |{accom:420,food:40,phone,10}|

``` 
//To access the the phone vaule of the first object

costs[2].phone

```
