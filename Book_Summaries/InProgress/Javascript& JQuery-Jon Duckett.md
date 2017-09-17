# Javascript & JQuery - Jon Duckett

--------

[Amazon Link](https://www.amazon.co.uk/d/Books/JavaScript-JQuery-Interactive-Front-end-Web-Development/1118531647/ref=sr_1_4?ie=UTF8&qid=1494148653&sr=8-4&keywords=Jon+Duckett)

-----

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

* Rules indication how the contents of elements should be shown in the browser
* Each rule has a selector & declaration block
* Selector state which elements the rule applies to
* Declaration block states how the element should be shown
* Declaration blocks have a property, and a property value, which is denoted as  `propertyName: propertyValue`

` .fruit {color:pink} `

* The `.fruit` is the selector
* The ` {color: pink;} ` is the `property name: property value`


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
	* Numeric Data types - Handles positives, negatives and decimals
	* String data types - Handles a series of characters
	* Boolean Data types - Handles `True` or `False` values

### Rules For Naming Variables

1. The name must start with either $, _ or a characters. **NEVER** numbers
2. You cannot use reserved words
3. Variables are case sensitive. So `score` and `Score` are different variables
4. Use a name that describes the information that it is storing, eg `homeAddress`
5. If you have more than two words in the variable, use a capital to separate the words, as shown in number 4.

### Arrays

* Stores a series of values.
* Should be used when you don't know how many variables will be needed, or when you need a large amount of variables.

### Creating Arrays

` var colors ;`
`colors = ['white','green','yellow'];`

### Accessing Values in Arrays

* Arrays are index based, starting at 0.
* To get the first element, its ` var firstItem=colors[0]`
* To get subsequent characters, increment the value in `[x]`.
* If you increment too far, where there is no more values in the array, you will get `index out of bounds.`

### Changing values in arrays

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

* The order of execution is BIDMAS (Brackets, Indices, Division, Multiplication, Addition and Subtraction)


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

```
function addTwoNumbers(numberOne,numberTwo){
return x+y
}
```

* The name of the function is `` addTwoNumbers``
* The parameters are   `` numberOne,numberTwo``
* The function when run will give back the value of `` x+y``
* to call the function, you will say `` addTwoNumbers(10,5) ``
* You can pass variables to a  function, `` addTwoNumbers(aNumber,anotherNumber)``

### Getting A Single Value Out Of a Function

*  You do this by assigning the value to a variable

```
var sumOfThreeAndFive = sum(3,5)
```

### Getting Multiple Values Out Of a Function
* Done by using an array
* You define the return statement as a variable that returns an array
* When calling the function, you define which value from the array you want back

```
 	function getSize(width, height, depth) {
	var area = width, height;
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
	var area = function(width, height) {
	return width *  height;
	};

	var size = area(3,4);

	```

### Immediately Invoked Function Expressions

* These are pronounced `` IIFE``
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
	* To assign the value of a property to an object
	* In event handlers and listenings to do something when the event occurs
	* To prevent conflicts between two scripts that might use the same variable name

### Variable Scope

* Local variables (Ones defined in function) -  can only be used in that function
* Global variables (Ones defined outside of functions) can be called in any function
* Global variables values are not changed with each function call, unless you modify the value in the function
* Local variables change values for each function call. (They are initialised when the function is called.

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

* A series of variables that are contained together.
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

### Accessing objects

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

**Creating the object then adding properties and methods.**

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

#### A function in Global Scope Function

* When a function is not declared within a object or function
* Will return the value of that object.

```
function windowSize() {
	var width = this.innerWidth;
	var height =  this.innerHeight;
	return [height, width];
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

* When a function is defined inside an object, it becomes a method, this refers to the object containing it.

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

* Refers the the passed value.

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

###  Arrays are Objects

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

|Property| Value                 |
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
//To access the the phone value of the first object

costs[2].phone

```
---------

### Built In Objects

1.  Browser Object Model
	This contains objects that represent the current browser window or tab.
2. Document Object Model
	This uses objects to create a representation of the current page. Creates a new object for each new element
3. Global Javascript Objects
	Represents things that the Javascript language needs to create a model of. Eg, dates and times.


-------

### Browser Object Model

* Window -  current browser/Tab
* Document - current webpage
* History - pages in browser history
* Location - current url of the page
* Navigator - Information about browser
* Screen - Devices display information

Window is the parent, where every other object is a child the window.

------
MAKE A DIAGRAM
### Document Object Model

Used to create a model of the current webpage

* `Document`(Root) -  Represents the page as a whole
	* `<html>`
		* `<head>`
			* `<title>`
		* `<body>`
			* `<div>`
				* attribute
			* `<p>`
			* text

-------

### Global Javascript Objects

* These are a bunch of individual objects that relate to different parts of the Javascript language
* Usually start with a capital letter

Example objects for data types:
* String
* Number
* Boolean

Example Objects to help with real world concepts:

* Date
* Math
* Regex

-----------------

### Data types Revisited

#### Primitive data types

1. String (Is a object)
2. Number (Is a object)
3. Boolean (Is a object)
4. Undefined (Is not a object)
5. Null (Is a object)

#### Complex Data Types

1. Objects


* Arrays and Functions are classified as objects.
* If they are objects, we can call functions on an object or use build in methods on these.
* To see all of these, look online.

--------

### Creating Instances of different types of objects

Follows the structure:

` var name = new objectType();`

Example:

` var today = new Date();`

-----------

## Decisions and Loops

Three key concepts:

* Evaluations - Where you analyze values to determine whether they match the expected results
* Decisions -  Using the result of evaluations, you can decide which path your script should go down
* Loops - Repeatedly doing the same steps.

--------------

### Evaluations

Done by IF-Then-Else

```
if (ConditionIsTrue){
do something
} else {
do something
}
```
-------------

### Type Coercion & Weak Typing

* Javascript converts data types behind the scenes to complete operations.
* This is known as type coercion
* Javascript is known as weak typing, as we can change the data type for a value.
* This can end up giving us wrong evaluations

-----

### Truthy & Falsy Values

* Because of type coercion, we can treat every value as either true or false

* Falsy values are treated as if they are false. This could be numbers that are 0, strings that are empty, variables that are not assigned to anything and so on.

* Truthly values are treated as if they are truth, they are the opposite or falsy values, eg, not 0, not empty, assigned to a value, true

--------------

### Checking Equality and Existence

* Objects are considered truthly if they exist, we can then check whether it is present in a page or not.

* There are two types of equality checkers:
	* == - this checks whether two objects are truthly or falsly
	* === - this is strict checking, this checks whether they share the same type

----------------

### Loops

Three main types

* for
* While
* Do while


#### For

` for ( var i = 0 ; i <10 ; i++){
do something
}
`
* You have to initialise a variable ( var i = 0)
* You then need to say when the loop should run (When i < 10)
* Then you say what should happen to I after the instruction is done (i++)
* Each time the instruction is done, I is incremented, when i = 10, the loop stops.

#### While

```
while (i <10){
do something
i++
}
```
* runs while the condition is true
* you need to increment or decrement the variable explicitly in the loop.

#### Do While

```
do {
dosomething
i++
} while (i < 1)
```

* similar to the while, but the while is declared after the do statement.

-----
## Document Object Model

-------
### What is the DOM?

* The DOM specifies how browsers should create a model of an HTML page, and how JavaScript can access and update the contents of a webpage while it is in the browser window.
* The DOM is represented as a tree.
* Parts of the webpage are represented as elements. Elements can have attributes and text values.

-------------
### Working with the DOM

Accessing and updating the DOM tree involves two steps:

1. Locate the node that represents the elements you want to work with
2. Use its text content, child elements and attributes.

#### Ways Of Accessing the elements

1. To select an individual element, use
	* getElementById(elements ID attribute)
	* querySelector(css selector)

2. To select multiple elements
	* getElementByClassName(class name)
	* getElementsByTagName(tagname)
	* querySelectorAll (Css selector)

3. Traversing between element nodes
	* parentNode
	* previousSibling/ nextSibling
	* firstChild/ lastChild

#### Working with those elements

* Access/update text of elements
	1.Select the `<li>` element
	2.use firstChild property to get the text node
	3.use the txt nodes only property (nodeValue) to get the text from the element

* Working with HTML Content
	1. innterHTML allows you to access child and text content
	2. to just work the text content, use textContent
	3. There are many methods that allow you to add/remove nodes, see DOM manipulation

* Access or update attribute values
	1.Can use the following:
		* hasAttribute()
		* getAttribute()
		* setAttribute()
		* remoteAttribute()


--------
#### Caching Dom Queries

Methods that find elements in the DOM are called DOM queries.
If you need to work with an element more than once, you should assign it to a variable

` var elementOne = document.getElementById('one); `

---------

#### Accessing Elements

When a DOM query returns more than on element, it will returned in a NodeList form.
This is a collected of nodes.

* Methods that return  a single element node:
	* getElementById('id');
	* querySelector('css selector')
* Methods that return one or more elements as a node list
	* getElementByClassName('class')
	* getElementByTagName('tagName')
	* querySelectorAll('css selector')

-------

#### Selecting Elements Using ID Attributes

```
/// Select the element and store it
var el = document.getElementById('one);
/// Change the value of the class attribute
el.className = 'cool';
```
-----

#### Nodelists

* NodeLists are treated as arrays
* Key difference is they are not actually arrays, they are a type of object called collection.
* You use ` item(index)` to return a specific node form the list, or the traditional array[x] syntax

------

#### Live and Static Nodelists

* A live NodeList occurs when your script updates the page, the NodeList is updated as well.
* A static NodeList occurs when the script updates your page, the NodeList is not updated as well.
* This occurs depending on what methods you use to get the elements.

-------

#### Selecting Elements Using Class Attributes

* use ` getElementsByClassName() `

---------
#### Selecting elements by tag name

* use ` getElementsByTagName() `

-------

#### Selecting Elements Using CSS Selectors

* `querySelector(selector) ` returns the first match
* ` querySelectorAll(selector)` returns all elements

------

#### Repeating Actions For An Entire Nodelist

*  Use for loops

```
var hotItems = document.querySelectorAll('li.hot');
for (var i = 0; i < hotItems.length; i++){
hotItems[i].className = 'cool';
}
```

-----

#### Traversing The DOM

Given you have an element node, you can select another element in relationship to it. This is known as traversing the DOM

You can do this with:

* parentNode
* previousSibling
* nextSibling
* firstChild
* lastChild

------

#### Whitespace Nodes

Some browsers add a text node whenever they come across white spaces between elements. This can cause issues when traversing the DOM

You can strip all the whitespace out of a page. This will make the page smaller and faster to load, but may make the code harder to read

Another way to deal  with this is to avoid using these DOM properties altogether.

JQuery for example is a solution for this.

------

#### Previous & Next Siblings

If there is a element that has siblings from the same parent, you can use `element.previousSibling` and ` element.nextSibling` to access these elements

----

#### First and Last Child

If there is a element that has siblings from the same parent, you can use ` element.firstChild` and `element.lastChild` to get these.

For example, if we have 4 `li` elements, this would not be suitable to get the third `li` element.

-------

#### How To Get/Update Element Content

* Navigate to the text node
	* This works best when the element contains only text.
* Work with the containing element
	* Allows you to access its text nodes and child elements.
* You will often be working with the property ` nodeValue`

---------
#### Accessing & Updating a text node with nodeValue


` document.getElementById('one').firstChild.nextSibling.nodeValue;
`

* In order to use nodeValue, you must be on a text node, not the element that contains the text.

---------------

#### Accessing and Changing a text Node

* You need to access the element node, then its text node.

* The text node will have a property called nodeValue which will return the text in the node.

* Can also use nodeValue property to update the text

```

//Get second list item
var itemTwo = document.getElementById('two');

//get its text content
var elText = itemTwo.firstChild.nodeValue;

//Change pine nuts to kale
elText = elText.replace('pine nuts', 'kale');

//Update the list item
itemTwo.firstChild.nodeValue = elText;

```

-----

#### Adding or Removing HTML Content

Two possible ways:

1. using the InnerHTML property of a node. (This is not advised)
2. DOM manipulation

#### Adding/Removing with HTML Content.

This should not be used due to security risks.

Approach:

1. Store the new content as a string variable, including the markup (To remove, make the string empty.)
2. Select the element whose content you want to replace
3. Set the elements innerHTML property to be the new String.

#### Adding/Removing with DOM Manipulation Methods

Approach:

1. Use a DOM method and store it in a variable
2. Use another DOM method to attach it /remove it from the DOM tree

Full Steps:

1. use createElement and store in a variable
2. Use createTextNode() and store in a variable
3. Use appendChild() to add it to the tree. AppendChild allows you to specify which element you want this to node added to, as a child of that node.

------

#### Adding An Element To The DOM Tree

```
var newEl = document.createElement('li');

var newText = document.createTextNode ('bob');

// Attach the new text node to the new element
newEl.appendChild(newText);

//Find the position where the new element should be added.
var position = document.getElementByTagName('ul')[0];

//Insert the new element into its position
position.appendChild(newEl);
```
-------

#### Removing An Element From the DOM Tree

1.  Store the element to be removed in a variable
2. Store the parent of the that element in a variable
3. Remove the element from its containing element.


```
//Element to remove
var removeEl = document.getElementsByTagName('li')[3];

//Its containing element
var containerEl = removeEl.parentNode;

//Removing the element
//containerEl= removeEl.parentNode;

```

-------

### Comparing Techniques: Updating HTML Content

* document.write()
	* Adds content that was not in the original source code.
	* Only works correctly when the page first loads
	* Generally do not use this.
* element.innerHTML
	* allows you to get/update the enter content of a element as a string.
	* This is faster than DOM manipulation when adding a large amount of elements
	* Simple way to remove all content from one element(pass it a blank string)
	* Should not be used to add content that has come from a user, this is a security risk
	* Event handlers can get broken when doing this.
* DOM manipulation
	* Good when a element has many siblings
	* Does not affect event handlers
	* Allows a script to add elements incrementally
	* Slower than innerHTML when doing many changes
	* Involves writing more code than other methods

----

### Cross-Site Scripting (XSS) Attacks

#### How XSS Happens

* When a user places malicious code into a website
	* When a user creates profiles or adds comments
	* When multiple authors may contribute to articles
	* When Data comes from a third party
	* When files and images can be uploaded

#### What can these attacks do?
