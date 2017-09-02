# Mastering Bash - Giorgio Zarelli

----




# Chapter 1: Let's start programming

## Intro

* There are two main types of commands:  Internal and external
* External command invoke external programs.
* When an external program is to be executed, bash creates a clone of itself, creating a new process
* For internal/builtin commands, bash exectues them without forking.
* This makes internal commands faster
* This also makes it possible that builtin commands can affect the terminals state, whereas external programs never can
* The shell works left to right
* The shell takes the first word from the command line as the name of the ocommand itself. Everything after is considered arguments
* Before assigning a variable, all text folllowing `=` is subject to the tilde expansion, parameter expansion, command substituation , artihmetic expansion and quote removal

## I/O Redirection

* Redirection is taking a stream that goes from one point to another and making it go somewhere else.
* In unix, each process which is not a daemon is supposed to be connected to a standard input, standard output, and standard error device
* Every device in Unix is represented by a file
* Streams are identified by a standard `POSIX file descriptor` (An interger used by the kernal as a handler to rrefer to them.
	* 0 =  `stdin` , which is read mode
	* 1 = `stdout`, which is write mode
	* 2 = `stderr`, which is write mode
* By using commands, you pass input to one of these 3.
	* Eg, `echo "hello"` is passed to stdout from stdin
* To pass a input to a file, use `>`
	* Eg: `echo "hello" > helloFile.txt`
* Get the contents of a file, use `cat fileName.extension`
* To add text to the end of a file, use `>>`
	* Eg: `" echo "Add this to a file" >> output_file.txt`
* To read from a file which without using `stdin`, use `<`
	* Example, reading a file and sorting it: ` sort < fileName`
* `|` Pipes the steam to stdout or stdeer, one process to another, so on.
* Everything in Unix is represented by afile, be it a device, a terminal or anything else.
* There is a special file called `/dev/null`, this is a sink hole. Anything sent to it gets lost




## Messing around with stdin, stdout and stderr

* `x <filename`: Opens a file in read mode and assigns the descriptor named x.  (eg, `1 < filename` or `2<filename`
* `1 > filename`: Redirects the standard output to filename. If it does not exist, it gets created, if it exists, it overwrites the pre-existing data
* `1>>filename`: Redirects the standard output to file name. if it does not exists, it creates it. If it does exist, it apppends the value to the end of the pre existing data
* `2>filename`: Redirects the standard error to filename. If it does not eist, it gets created, if it eists, the pre-existing data is overwritten
* `2 >> filename`: Redirects the stand error to file name. If not created, creates file, if file exists, appends it to the end of the file
* `& > filename`: Redirects **both** stdout and stderr to filename. Firstly redirects the error. If it does not exist, creates the file, if it exists, overwrites the file
* `2>&1`: Redirects the stderr to the stdout. All error messages will be send to stdout
* `y>&x`: Rediects the file descriptor 1 that is associated with the stdout to the file pointed by the descriptor x, so whatever hits the standard output will be wrirten in the file pointed by x
* `>&x`:Redirects the file descriptor 1 that is associated with the stdout to the file pointed by the descriptor x, so whatever hits stdout will be wrirten in the file pointed to by  x
* `x<> filename` Opens a file in read/write mode and assign the descriptor x to it. Iff the file does not exist, it is created, and if the descriptor is omitted, it desfaults to 0 (stdin)
* `x<&-` Closes the file opened inr ead mode and associated with the descriptor x
* `0<&-` or `<&-`: Closes the file opened in read mode and associated with the descriptor 0 (stdin), which then closes stdin
* `x>&-` Closes the file opened in write mode and associated with the descriptor x
* `1>&-` or `>&-`: Closes the file opened in write mode and associated with the descriptor 1, the stdout, which is then closed
* To find out what file descriptors (Stdin,out,err) are assoicated with a file, use `ls -lah /proc/PROCESSID/fd`
	* Where the process ID is the id of an open process (eg, chrome)


Example script:

```
echo "echo \ "This should go under the sha-bang\"" >test.sh
```

## Calling Your Script

* You need to ensure that your script has the correct permissions before calling it
* You find out the permissions by using `ls -lah scriptName.fileExtension`
* This will return `-Type-User--Group--Others--`
	* Type can have the either `d`, for directory, or `-` which is file
	* User, group and others can have either `r` for read, `w` for write, or `x` for execute (Note, you can have all three of these on a single file!)
	* The same can be used for directories, but `x` means you can traverse the directory, `r` means that you can enumerate the contents of it, and `w` means you can modify the attributes of the directory and removes the entries that are eventually in it.

File type indicators

* `-` = Regular file
* `b` = Block file
* `c` = Character file
* `d` = Directory
* `l` =  Symbolic link
* `p` = Named pipe (FIFO)
* `s` =Socket

Unmask

* The build in command returns a binary number which represents the premissions of the current directory you are in:
* `r` = 100 = 4
* `w` = 010 = 2
* `x` = 001 = 1
* You add the final decimals together and use `chmod value fileName` to change its permissions
* You can also use `chomod u+rwx filename` to change the permissions, whcih r w and x are above.
* **NOTE: You must cacluate read, write and execution grands in tiplets, one of the owner of the file (u), one for the group (g) and one for others (o)**


Examples 

Changing file permissions for the user

`chmod u+rwx filename`
`chmod 7 filename`
(7 here represents user in the format UserGroupOther)

Changing file permissions for User, group and other

`chmod 764 fileName`
`chmod 774 fileName`

Changing file permissions for user and other

`chmod 707 fileName`


* It should be noted that files have a set of base permissions that are used when anything is created (Not going to cover this, look up UID and Set User ID (SUID), Set GID (Group ID)


## Debugging

* you can use `df -h` 
* This returns information about the file or script you are running.

Eg 

`df -h testFile.txt`

## Variables

* Variables have no types
* To assign a variable, use the format `LABEL = value`

eg

`HELLO_WORLD = hello`

* To get the value in a variable, use `$VARIABLE_NAME` or `${VARIABLE_NAME}`
* You will want to use the second example when concatenating anything to it 

Example

`echo {HELLO}World`

* Variables content is only accessible after the value has been assigned. 
* Content of a variable instanced inside a function is not available when it is defined in the function, but when the function is invoked.
* Variables marked with `local` and are defined in a function are only available inside that function and the function has been invoked

## Environment Variables


* To list al environment variables used, use `env`
* You can create environment variables by using the `export` command

Example

```
export TEST_VAR = awesome
echo ${TEST_VAR}
```

* To unset a environment variable, use `unset VARIABLE_NAME`

Example

`unset TEST_VAR`

* Unsetting works for all variables, they do not have to be environment variables , you can do this with `unset -v variableName`
* There are some already created environment variables we may want to modify/use
	* `BASH_VERSION` = Version of the current bash session
	* `HOME` = Home directory of the current user
	* `HOSTNAME` = Name of the host
	* `LANG` = Local used to mange the shell
	* `PATH` = The search path for the shell
	* `PS1` = Prompt configuration
	* `PWD` = Path to current directory
	* `USER` = Name of the currently logged in user
	* `LOGNAME` = Same as user

* You can use ` env -i` to pass the variable we want

Example

```
env -i PATH=HELLO LOGNAME=whoami/user/bin/env
```

## Variable Expansion

* Used to access and actualy change the content of a variable or parameter
* Simpliest way is to assign the value then reference it with a dolla sign

Example

` x = 1; echo $x`

* We can also also set the default value of  a variable by either doing :  `${variable-default}` or `${variable:-defaut}`
* If the variable is not set, and we have set a default value, it will return the default value
* `${variable-default}` ignores the fall back if the variable value is null
* `${variable:-defaut}` will use the fallback value if the variable is null


Example

`echo "${x:-20}"`

* `${variable:+default}` or `${variable+default}` checks whether the variable exists and is not null, if it does exist and is not null, return the default value, otherwise return null


## Pattern Matching Against Variables

* To declare an array `variableName=( itemOne itemTwo itemThree)`
* To access an item in an array: `${variableName[index]}`
* If you want to return all variables that do not match a pattern, use `${listName#pattern}`
* To return specified index, use `${myVariable#startIndex*EndIndex}`
* To remove the shortest occurance of a pattern, use `${myVariable%pattern}`
* To remove rthe longest occurance of a pattern from the end, use `${variable%%pattern}`


# Operators

## Arithmetic Operators

* Basic Arithmetic operators:
	* +
	* -
	* *
	* /
	* %
	* ** (Exponent)

## Assignment Operators

* `+=` Concatenates a value. Eg `x=10; x+=10` will return 1010
* `-=` will remove the value from the variable it is used against. 
* `*=` multiples the value of the variable for the number given and reassigns it
* `/=` Divides the value of the variable for a given number, and reassigns the new value
* `%=`, divides the value of the variable for a given value, but reassigns the remainded to that variable
* `++` and `--` increase and decrease the variable by 1

## Comma Operator (,)

* This chains together arithmetic operators.
* All operations are evaluated, but the value of the last one is returned

## Exit Codes

* `0` = Success
* `1` = Failure
* `2` = Misuse of builtin
* `126` = Command not executable
* `127` = Command not found 
* `128` Invalid Argument
* `128+x` = Fatal Error exit with signal x
* `130` = Execution terminated by Control + c
* `255` = Exit state out of boundary (0-255)


## Exiting a Script

* Use `exit EXITCODE`
Eg `exit 20`

# Testing (CONTINUE)

## If Then Else

* Ifs have the following structure: `if ....fi`
* Can have Else, elif, then

Example

```
if ......
then
dosomething
elif ....
then
dosomething
else 
dosomething
fi
```

# Quoting and Escaping

## Special Characters

* Use `\` before a special character to escape it
* `#` Represents a comment
* `;` seperates commands
* `;;` is a case construct option terminator (Will find out what this is later...) (Think of it as a seuqnece of if/then/else)
* `;;` If the condition is matched, the other options will not be tested
* `;&` This makes the execution continue with the commands associated to the next condition
* `;;&` This makes the shell check the option and execute the associated commands if the condition is matched
* `.` if used in the shell executes a file, if in a script, loads the referenced file content
	* eg `. comment.sh`
* `..` avoids the interpretation of most of the special characters in the shell (More later)
* `...` avoids the interpretation of all special characters by the shell
* `,` chains together artihmetic operations or strings
* `,,` and `,()` forces a lower case conversion in the parameter substituion
* `^^` and `^()` forces upper case conversion in the parameter substituion
* `/` has two uses:
	* File name separator in paths
	* Arithmetic operator for divison
* `...` command substituion, it assigns stdout command to a variable
* `!` negates or reverses a test or an exit status
* `*` wildcard when looking files (File name expansion in this way is known as globbing)
* `**` matches filenames AND directories
* `?` test operator
* `$` variable substituion
* `${}` parameter substituion
* `$'..'` Quoted string expansion, used to expand escaped octal or hex values in unicode of ASCII
* `$*` and `$"` positional parameters
* `$?` gets the eit status
* `$$` holds the process id (PID) of the script 
* `[[]]` Expressions
* `[]` array index
* `[]` character ranges
* `$[...]` integer expansion
* `(((.)))` integer expansion
* `<<` here document - forces the shell to read input up till a specific word

Example

```
cat << DELIMITER
assd
asdasdsa
asdasdas
DELIMITER
```

* `""` weak quoting, they prevent the interpretation by the shell of all metacharacters except for $, ", ' and \
* `''` strong quoting, does not interpret any meta characters
## Matching characters

* `[:alnum:]` matches both alphabetic and numberic characters
* `[:alpha:]` matches only alphabetic characters
* `[:blank:]` matches only a tab or space
* `[:cntrl:]` matches only control characters
* `[:digit:]` matches only digits between 0  to 9
* `[:graph:]` matches any the character that has  a value between 33 and 126 in the ASCII table
* `[:lower:]` matches alphabetic characters in lower case
* `[:print:]` matches the graph, but also matches the range is from 32 to 126 including the space characters too
* `[:space:]` matches the space and horizontal tabs
* `[:upper:]` matches alphabetic characters in upper case
* `[:xdigit:]` matches digits, but in a deadecimal notation


Example

```
case "$number" in
	[[:digit:]]
	return 0
```

## Keywords

* Following words are reserved:
	* `compgen -k`
	* `if `
	* `then`
	* `else `
	* `elif`
	* `fi`
	* `case`
	* `esac`
	* `for`
	* `select`
	* `while`
	* `until `
	* `do `
	* `done`
	* `in `
	* `function`
	* `time`
	* `{`
	* `}`
	* `!`
	* `[[`
	* `]]`
	
	
	
# Menus, Arrays, and Functions