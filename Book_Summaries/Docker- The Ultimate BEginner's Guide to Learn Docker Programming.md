# Docker: The Ultimate BEginner's Guide to Learn Docker Programming

## Docker Overview

* First Introduced to the public in 2013.
* Uses "Containers", containers contain all the software they need to run without minimal outside help.
* Containers are independant of each other. So containers can run in parrallel without issues.
* To make the most of docker, you need to generate "base" images for each system layer. Images then can be reused to keep consistencey between containers? (Check)
* Docker works with Windows, macOS and Linux

## Docker Admin Guide

### Congifuring Docker

* The docker daemon will run a configuration function. This function can be changed via the process manager
* `dockerd` command will start the Daemon running the directory which by default with work with the Unix socket that is already stored in the Docker directory
* To run the daemon directly without the use of the process manager, you need to configure the options that will let you run the command directly. A few of these options are:
	* `tls = false` : The TLS will be enabled or disabled, and the system will automatically put it to false
	* `H -host = []` : the sockets for the daemon are going to be connected
	* `d -debug = false` : debug mode will be set to false


## Docker Containers

* Containers work by having its own os and processes.
* These act as individual systems, which can be ran on one system
* You want to ensure that the name space is isolated. This will ensure that you will have all of the resources that the application will require



CONTINUE