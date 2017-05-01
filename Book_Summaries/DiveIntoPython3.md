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

